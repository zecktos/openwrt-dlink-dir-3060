# openwrt dlink dir 3060
this repo holds [pre-built openwrt firmware](https://github.com/zecktos/openwrt-dlink-dir-3060/releases) and a patch to build current openwrt for the dlink dir 3060.  
All the work was made by Lucky1 in the [openwrt forum](https://forum.openwrt.org/t/adding-openwrt-support-for-dir-3060/94335/42). I just made a patch file out of it.  

## build
Download and update the openwrt sources
```
git clone https://git.openwrt.org/openwrt/openwrt.git
cd openwrt
git pull
 ```
Select code revision
```
git branch -a
git tag
git checkout v22.03.3
```
Download and apply patch
```
curl https://raw.githubusercontent.com/zecktos/openwrt-dlink-dir-3060/main/DIR-3060.patch -o DIR-3060.patch
git apply DIR-3060.patch
```
Update the feeds
```
./scripts/feeds update -a
./scripts/feeds install -a
```
Download and make config
```
curl https://raw.githubusercontent.com/zecktos/openwrt-dlink-dir-3060/main/diffconfig -o .config
make defconfig
```
build image

```
make download
make -j $(nproc)
```
