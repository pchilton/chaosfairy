# mobile

React Native skeleton for the chaosfairy Android / iOS apps.

## Prerequisites

React Native requires a Node.js/NPM toolchain, a JDK, and the Android SDK (via Android Studio) for Android builds. This project uses [ASDF](https://asdf-vm.com/) to manage Node.js and Java versions.

### 1. ASDF

Install ASDF (if you have not already):

```bash
git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.14.0
```

Add ASDF to your shell (e.g. `~/.bashrc`, `~/.zshrc`):

```bash
. "$HOME/.asdf/asdf.sh"
. "$HOME/.asdf/completions/asdf.bash"
```

### 2. Node.js + NPM (via ASDF)

Add the nodejs plugin and install the version pinned in `.tool-versions`:

```bash
asdf plugin add nodejs https://github.com/asdf-vm/asdf-nodejs.git
asdf install
asdf reshim
```

Verify:

```bash
node --version   # v24.22.2
npm --version
```

NPM ships with Node, so no separate NPM install is needed. The `engines` field in `package.json` requires Node >= 22.11.0.

### 3. Java / JDK (via ASDF)

Android Studio and the React Native Gradle plugin require a JDK. This project pins Java 17 (openjdk-17.0.2), which is the recommended JDK for the Android Gradle Plugin used here.

```bash
asdf plugin add java https://github.com/halcyon/asdf-java.git
asdf install
asdf reshim
```

Verify:

```bash
java -version
```

Set `JAVA_HOME` if your toolchain expects it:

```bash
export JAVA_HOME=$(asdf where java)
```

### 4. Android Studio

Download and install [Android Studio](https://developer.android.com/studio).

Once installed, open Android Studio and install the required SDK components via **SDK Manager** (or `sdkmanager`):

- Android SDK Platform (latest stable, e.g. API level 35)
- Android SDK Build-Tools (latest)
- Android Emulator
- Google Play Intel x86 Atom_64 System Image (or any emulator system image you plan to run)

Configure environment variables (add to `~/.bashrc`, `~/.zshrc`, etc.):

```bash
export ANDROID_HOME=$HOME/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/platform-tools
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
```

Then:

```bash
source ~/.bashrc
```

Accept Android SDK licenses:

```bash
yes | sdkmanager --licenses
```

Verify the Android SDK is visible:

```bash
sdkmanager --list_installed
```

## Project setup

Install JavaScript dependencies:

```bash
cd mobile
npm install
```

## Running the app

Start the Metro bundler:

```bash
npm start
```

Run on Android (requires an emulator running or a device connected with USB debugging enabled):

```bash
npm run android
# or
npx react-native run-android
```

Run on iOS (macOS only, requires Xcode):

```bash
npm run ios
# or
npx react-native run-ios
```

## Verification

React Native ships with a doctor command to check your environment:

```bash
npx react-native doctor
```

## Version pins

Node.js and Java versions are pinned in `mobile/.tool-versions` and managed by ASDF:

```
nodejs 24.22.2
java openjdk-17.0.2
```

Run `asdf install` inside `mobile/` to install the pinned versions.
