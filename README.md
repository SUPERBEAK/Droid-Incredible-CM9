# CM9 for the Droid Incredible

## Info

|||
|-----------------------------------:|:--------------------------|
|**Discussion thread**: | http://forum.xda-developers.com/showthread.php?t=1558923
|**Bug List**:		| https://docs.google.com/spreadsheet/ccc?key=0ArO-AoPZJh5KdHd4N3UxdzBObEtEbWViSVBaVlhVTFE#gid=0
|**Original build instructions**:|http://forum.xda-developers.com/showpost.php?p=23905364&postcount=2

## Building 

### Initialize
[setup linux/OS X](http://source.android.com/source/initializing.html) - Please note: it must be sun-java-6, not openjdk

### Download Evervolv sources

```bash
mkdir ~/evervolv
cd ~/evervolv/
curl https://dl-ssl.google.com/dl/googlesource/git-repo/repo > ~/bin/repo
chmod a+x ~/bin/repo
repo init -u git://github.com/Evervolv/android.git -b ics
repo sync -j16
```

### Download CM9 sources

```bash
mkdir ~/cm9
cd ~/cm9/
curl https://dl-ssl.google.com/dl/googlesource/git-repo/repo > ~/bin/repo
chmod a+x ~/bin/repo
repo init -u git://github.com/CyanogenMod/android.git -b ics
repo sync -j16
```

### Download Droid Incredible device tree

```bash
git clone https://drkhd@github.com/drkhd/Droid-Incredible-CM9.git github/inc
mkdir -p device/htc/ vendor/htc/
cd device/htc
ln -s ../../github/inc/device inc
cd ../../vendor/htc
ln -s ../../github/inc/vendor/ inc
cd ../../
./vendor/cm/get-prebuilts
```

### Copy and overwrite from Evervolv to CM9
```bash
device/htc/common
vendor/htc/inc
hardware/qcom
hardware/msm7k
```

### Build
```bash
cd ~/cm9
. build/envsetup.sh && brunch inc
```
