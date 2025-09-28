# 补丁文件

大部分补丁位于本仓库的mesa文件夹（来自glibc package仓库）

由于glibc仓库的驱动是老版本且长时间没有进行更新，部分补丁可能会在后续版本逐渐失效

### 先通过```patch --diy-run -p1 < path/to/XXX.patch``` 试运行一遍！




# 构建参数

```bash
meson setup builddir \
-Dprefix=~/build \
-Dbuildtype=release \
-Dplatforms=x11,wayland \
-Dgallium-drivers=freedreno,virgl,zink,panfrost,swrast,llvmpipe \
-Dvulkan-drivers=freedreno,panfrost,swrast,virtio \
-Degl=enabled \
-Dgles1=disabled \
-Dgles2=enabled \
-Dglvnd=enabled \
-Dglx=dri \
-Dllvm=enabled \
-Dosmesa=true \
-Dshared-glapi=enabled \
-Dgallium-extra-hud=true \
-Dgallium-va=enabled \
-Dgallium-vdpau=enabled \
-Dgbm=enabled \
-Dvulkan-layers=device-select,overlay \
-Dfreedreno-kmds=kgsl \
-Dlibunwind=disabled \
-Dvalgrind=disabled \
-Dmicrosoft-clc=disabled
```

之所以没有 ```-D dri3=enabled```在更新的版本中已删除

# 感谢

## 参数整合与补丁的参考

[lfdevs/mesa-for-android-container](https://github.com/lfdevs/mesa-for-android-container)

==========================

[termux-pacman/glibc-packages](https://github.com/termux-pacman/glibc-packages)

- [gpkg/mesa](https://github.com/termux-pacman/glibc-packages/tree/main/gpkg/mesa)

