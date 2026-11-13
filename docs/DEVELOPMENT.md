
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
```

