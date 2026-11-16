
## Prerequisites

React Native requires a Node.js/NPM toolchain, a JDK, Ruby (for CocoaPods on iOS), and the Android SDK (via Android Studio) for Android builds. This project uses [ASDF](https://asdf-vm.com/) to manage Node.js, Java, and Ruby versions.

### 1. ASDF

Install ASDF (if you have not already):

```bash
git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.15.0
```

Add ASDF to your shell (`~/.bashrc`):

```bash
. "$HOME/.asdf/asdf.sh"
. "$HOME/.asdf/completions/asdf.bash"
```

### 2. Node.js + NPM (via ASDF)

Add the nodejs plugin

```bash
asdf plugin add nodejs
asdf install nodejs 24.22.2
asdf global nodejs 24.22.2
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
asdf plugin add java
asdf install java openjdk-17.0.2
asdf global java openjdk-17.0.2
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

### 4. Ruby (via ASDF)

iOS builds use CocoaPods, which requires Ruby. This project pins Ruby 3.4.10.

```bash
asdf plugin add ruby
asdf install ruby 3.4.10
asdf global ruby 3.4.10
asdf reshim
```

Verify:

```bash
ruby --version   # ruby 3.4.10
gem --version
```

Install bundler and CocoaPods:

```bash
gem install bundler
gem install cocoapods
asdf reshim
```


### 5. Android Studio

Download and install [Android Studio](https://developer.android.com/studio).

Once installed, open Android Studio and install the required SDK components via **SDK Manager** (or `sdkmanager`):

- Android SDK Platform (latest stable, e.g. API level 35)
- Android SDK Build-Tools (latest)
- Android Emulator
- Google Play Intel x86 Atom_64 System Image (or any emulator system image you plan to run)

Configure environment variables (add to `~/.bashrc`):

```bash
export ANDROID_HOME=$HOME/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/platform-tools
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/cmdline-tools/latest/bin
```

Then:

```bash
source ~/.bashrc
```

Verify the Android SDK is visible:

```bash
android sdk list
```


### 6. iOS Pods

```bash
cd mobile/ios/
bundle exec pod install
```
