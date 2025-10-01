# 补丁文件

大部分补丁位于本仓库的mesa文件夹（来自glibc package仓库）

由于glibc仓库的驱动是老版本且长时间没有进行更新，部分补丁可能会在后续版本逐渐失效

### 先通过```patch --dry-run -p1 < path/to/XXX.patch``` 试运行一遍！

# v25版本

# kgsl 0011号补丁疑似失效，构建时存在无法避免的语法错误 <= 25.2.3

# v25/wsi补丁无法应用在25.1

```bash
meson setup builddir \
-Dprefix=~/build \
-Dbuildtype=release \
-Dplatforms=x11,wayland \
-Dgallium-drivers=freedreno,virgl,zink,panfrost,llvmpipe \
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
-Dfreedreno-kmds=kgsl,msm \
-Dlibunwind=disabled \
-Dvalgrind=disabled \
-Dmicrosoft-clc=disabled
```

# virglrenderer



#### 补丁取代

```mesa/wsi-termux-x11-v3.patch```=>```v25/wsi-termux-x11-fix2.patch```

```mesa/0014-freedreno-HACK-GL_ARB_timer_query.patch```=>```v25/0014-freedreno-HACK-GL_ARB_timer_query2.patch``

```mesa/0012-freedreno-drm-Add-more-APIs-to-per-backend-API.patch```=>```v25/0012-freedreno-drm-Add-more-APIs-to-per-backend-API2.patch```




# 构建参数

```bash
meson setup builddir \
-Dprefix=~/build \
-Dbuildtype=release \
-Dplatforms=x11,wayland \
-Dgallium-drivers=freedreno,virgl,zink,panfrost,llvmpipe \
-Dvulkan-drivers=freedreno,panfrost,swrast,virtio \
-Degl=enabled \
-Dgles1=disabled \
-Dgles2=enabled \
-Dglvnd=enabled \
-Dglx=dri \
-Dllvm=enabled \
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
被弃用的参数

- shared-glapi
- osmesa

# 感谢

## 参数整合与补丁的参考

[lfdevs/mesa-for-android-container](https://github.com/lfdevs/mesa-for-android-container)

==========================

[termux-pacman/glibc-packages](https://github.com/termux-pacman/glibc-packages)

- [gpkg/mesa](https://github.com/termux-pacman/glibc-packages/tree/main/gpkg/mesa)

==========================

[termux/termux-packages（非glibc环境）](https://github.com/termux/termux-packages)

-[packages/mesa](https://github.com/termux/termux-packages/tree/master/packages/mesa)

-[xMeM patch（非Glibc环境）](https://github.com/xMeM/termux-packages/commit/401982b8d9eaef70669762bfff2a963341c65e52)
