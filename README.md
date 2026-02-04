# local_manifests
## How to setup and build ROM
- ### Ubuntu:
### 1. Get Repo tool:
```bash
sudo apt update
```
```bash
sudo apt install git repo
```
### 2. Get dependencies to build ROM:
```bash
sudo apt update
```
```bash
sudo apt install -y bc bison build-essential ccache curl flex g++-multilib gcc-multilib git git-lfs gnupg gperf imagemagick lib32ncurses-dev lib32readline-dev lib32z1-dev libelf-dev liblz4-tool libncurses6 libncurses-dev libsdl1.2-dev libssl-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev python3 python-is-python3 libncurses6 python3-pip unzip vim openjdk-17-jdk repo
```
### 3. Choose where to store Android ROM source with ```cd``` command
### 4. Grab ROM manifest and initialize Android:
```bash
repo init -u [ROM manifest] -b [Branch] --git-lfs
```
For example let's download Android 16 QPR0 LineageOS
```bash
repo init -u https://github.com/LineageOS/android.git -b lineage-23.0 --git-lfs
```
### 5. Download needed device manifest in this repository:
- Choose needed device manifest and download raw file. After that put the downloaded manifest where you setup the Android ROM source there
```
./android/.repo/local_manifests
```
### 6. Sync (Download) the Android ROM source:
```bash
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
```
```-c``` flag tells Repo to only sync current branches (decreases load)

```-j$(nproc --all)``` flag tells Repo how much threads to use when syncing. ```$(nproc --all)``` returns total available CPU threads

```--force-sync``` flag tells Repo to fix issues without user confirmation

```--no-clone-bundle``` flag tells Repo to not download bundles

```--no-tags``` flag tells Repo to not fetch tags

### 7. Start the build:
- Prepare the enviroment
```bash
source build/envsetup.sh
```
- Prepare build system to build device
```bash
breakfast [device]
```
- Begin building
```bash
brunch [device]
```
