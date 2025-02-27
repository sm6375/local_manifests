
# Build for PixelOS.

## starting repo's 

```sh
mkdir pixelos
cd pixelos

repo init -u https://github.com/PixelOS-AOSP/manifest.git -b fifteen
repo sync

git clone https://github.com/sm6375/local_manifests -b main .repo/local_manifests
repo sync
```

## fixing vendor_gms
```sh
rm -rf vendor/gms

git clone https://gitlab.com/pixelos-aosp/vendor_gms vendor/gms

rm -rf .repo/projects/vendor/gms.git
rm -rf .repo/project-objects/*/android_vendor_gms.git
```

## preparing construction 
```sh
. build/envsetup.sh
lunch aosp_bangkk-ap4a-user
mka bacon -j$(nproc --all)
```

## ref for signing build
- [pixelos doc](https://blog.pixelos.net/docs/JoinTheTeam/SigningBuilds)
