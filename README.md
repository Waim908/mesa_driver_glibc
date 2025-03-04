# Turnip
构建参数
```meson build64/ --prefix ~/build -D platforms=x11,wayland -D gallium-drivers=swrast,virgl,zink,freedreno -D vulkan-drivers=freedreno -D egl=enabled -D gles2=enabled -D glvnd=enabled -D glx=dri -D libunwind=disabled -D osmesa=true -D shared-glapi=enabled -D microsoft-clc=disabled -D valgrind=disabled -D gles1=disabled -D freedreno-kmds=kgsl -D buildtype=release```
之所以没有 ```-D dri3=enabled```在mesa25.1.0中已删除
