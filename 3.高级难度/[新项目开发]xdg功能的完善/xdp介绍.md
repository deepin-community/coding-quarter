# xdg-desktop-portal 介绍

xdg-desktop-portal, 下面简称xdp,是针对flatpak或者其他可能的桌面框架的前端服务，后端由桌面环境自己实现，这部分称为xdg-desktop-impl-portal,前后端组合成为xdg-desktop-portal整个项目。具体介绍可以从[xdg-desktop-portal](https://github.com/flatpak/xdg-desktop-portal)获取到源代码。

## 在现代桌面环境起到的功能

xdp自我介绍为主要提供给flatpak沙盒软件权限控制和访问宿主机的接口，但桌面用户(主要为wayland用户)更熟悉的是它提供的截图和录屏功能。wayland的窗口管理器由于高度定制，不能统一通过X11协议获取到图片和流，在xdp没有出现之前都是各个桌面环境提供自己的截图功能，截图工具不能通用，flameshot等软件由于没有统一的接口，实现wayland截图困难，如果强行根据不同桌面环境实现截图，会带来屎山。

xdp出现后，开发者并不需要研究X11和桌面窗口管理器的接口和协议，只需要调用已知的dbus接口。同时桌面可以定制更多功能，比如实现有桌面环境特点的popup窗口，或者依照app\_id设置黑名单软件，达到权限控制和隔离，或者实现在某些黑名单软件调用截图发送假的图像，都是可以做到的。

xdp的特点是权限控制，以及桌面环境的高度可定制性。同时其以前的一些复杂的实现细节交给了桌面环境去定制，避免了桌面应用开发者去研究例如X11等古老晦涩的代码，桌面开发者只需要会调用dbus接口，就可以实现桌面环境需要的功能。

## xdp是如何运作的

对于xdp而言，最重要的是两个文件

```
/usr/share/xdg-desktop-portal/portals/<name>.portal 
/usr/<libexec>/<tool-name>
```

如果有看过xdp目录结构的话应该很熟悉，这里以最简单的wlr-portal为例子说说明

wlr.portal
```
[portal]
DBusName=org.freedesktop.impl.portal.desktop.wlr
Interfaces=org.freedesktop.impl.portal.Screenshot;org.freedesktop.impl.portal.ScreenCast;
UseIn=wlroots;sway;Wayfire;river;phosh;
```
portal的说明文件是很简单的ini文件，包括3个key值:

* DBusName 这个key值说明了这个protal服务的DBus的名称，即调用服务的位置
* Interfaces 这个key值记录了这个protal允许被启动的接口
* UseIn 这个key是 $XDG\_CURRENT\_DESKTOP的环境变量，如wlr的说明，这个portal可以在4种桌面环境运行

另外重要的文件就是运行的二进制文件，这个二进制文件实现了必要的dbus接口，并注册到了\<name\>.portal中记录的DBusName上。如果想要调用这个XDP的服务二进制程序需要在后台运行。

为了确保二进制程序在需要时候被启动，一般的xdp的包会引入另外两个文件

```
xdg-desktop-portal-wlr /usr/
xdg-desktop-portal-wlr /usr/lib/
xdg-desktop-portal-wlr /usr/lib/systemd/
xdg-desktop-portal-wlr /usr/lib/systemd/user/
xdg-desktop-portal-wlr /usr/lib/systemd/user/xdg-desktop-portal-wlr.service
xdg-desktop-portal-wlr /usr/lib/xdg-desktop-portal-wlr
xdg-desktop-portal-wlr /usr/share/
xdg-desktop-portal-wlr /usr/share/dbus-1/
xdg-desktop-portal-wlr /usr/share/dbus-1/services/
xdg-desktop-portal-wlr /usr/share/dbus-1/services/org.freedesktop.impl.portal.desktop.wlr.service
xdg-desktop-portal-wlr /usr/share/licenses/
xdg-desktop-portal-wlr /usr/share/licenses/xdg-desktop-portal-wlr/
xdg-desktop-portal-wlr /usr/share/licenses/xdg-desktop-portal-wlr/LICENSE
xdg-desktop-portal-wlr /usr/share/man/
xdg-desktop-portal-wlr /usr/share/man/man5/
xdg-desktop-portal-wlr /usr/share/man/man5/xdg-desktop-portal-wlr.5.gz
xdg-desktop-portal-wlr /usr/share/xdg-desktop-portal/
xdg-desktop-portal-wlr /usr/share/xdg-desktop-portal/portals/
xdg-desktop-portal-wlr /usr/share/xdg-desktop-portal/portals/wlr.portal
```

如图所示，包内除了必要的可执行文件和portal说明文件外，还引入了dbus的service文件和systemd user文件。

org.freedesktop.impl.portal.desktop.wlr.service
```
[D-BUS Service]
Name=org.freedesktop.impl.portal.desktop.wlr
Exec=/usr/lib/xdg-desktop-portal-wlr
SystemdService=xdg-desktop-portal-wlr.service
```

以wlr的xdp包为例子，当dbus服务尝试调用org.freedesktop.impl.portal.desktop.wlr时候，其会去启动xdg-desktop-portal-wlr.service 的systemd服务

xdg-desktop-portal-wlr.service
```
[Unit]
Description=Portal service (wlroots implementation)
PartOf=graphical-session.target
After=graphical-session.target
ConditionEnvironment=WAYLAND_DISPLAY

[Service]
Type=dbus
BusName=org.freedesktop.impl.portal.desktop.wlr
ExecStart=/usr/lib/xdg-desktop-portal-wlr
Restart=on-failure
```

之后所示的systemd服务就会被启动。这样设计的好处是用户没必要自己去控制服务的启动，同时可以通过systemd的日志查看服务的状态。


## 环境配置和调试

需要将\<name\>.portal文件放到/usr/share/xdg-desktop-portal/portals下，重新启动xdg-desktop-portal的前端，这个portal的信息就被读取了。xdg-desktop-portal的代码中/usr/share/xdg-desktop-portal是明文写的绝对路径，所以/usr/local的prefix是不起作用的。

调试阶段不建议配置dbus 服务和systemd服务，这样服务的启动为自动状态，不受到控制，也难以debug。

## 示例项目

目前成熟的xdg-desktop-portal后端项目有6个

* [xdg-desktop-portal-kde](https://invent.kde.org/plasma/xdg-desktop-portal-kde)
* [xdg-desktop-portal-gtk](http://github.com/flatpak/xdg-desktop-portal-gtk)
* [xdg-desktop-portal-gnome](https://gitlab.gnome.org/GNOME/xdg-desktop-portal-gnome)
* [xdg-desktop-portal-pantheon](https://github.com/elementary/portals)
* [xdg-desktop-portal-wlr](https://github.com/emersion/xdg-desktop-portal-wlr)
* [xdg-desktop-portal-lxqt](https://github.com/lxqt/xdg-desktop-portal-lxqt)

其中kde的后端项目同样使用qt，适合成为参考。
