# Android GUI for [WireGuard](https://www.wireguard.com/)

**[Download from the Play Store](https://play.google.com/store/apps/details?id=com.wireguard.android)**

This is an Android GUI for [WireGuard](https://www.wireguard.com/). It [opportunistically uses the kernel implementation](https://git.zx2c4.com/android_kernel_wireguard/about/), and falls back to using the non-root [userspace implementation](https://git.zx2c4.com/wireguard-go/about/).

## Building

In case you get error building:

```
unsupported ELF machine number 183
```
checkout the branch `remotes/origin/lr/for-jason`

```
$ git clone --recurse-submodules https://github.com/antnks/wireguard-android
$ cd wireguard-android
$ git checkout remotes/origin/lr/for-jason
$ ./gradlew assembleRelease
```

macOS users may need [flock(1)](https://github.com/discoteq/flock).

## Embedding

The tunnel library is [on Maven Central](https://search.maven.org/artifact/com.wireguard.android/tunnel), alongside [extensive class library documentation](https://javadoc.io/doc/com.wireguard.android/tunnel).

```
implementation 'com.wireguard.android:tunnel:$wireguardTunnelVersion'
```

The library makes use of Java 8 features, so be sure to support those in your gradle configuration with [desugaring](https://developer.android.com/studio/write/java8-support#library-desugaring):

```
compileOptions {
    sourceCompatibility JavaVersion.VERSION_1_8
    targetCompatibility JavaVersion.VERSION_1_8
    coreLibraryDesugaringEnabled = true
}
dependencies {
    coreLibraryDesugaring "com.android.tools:desugar_jdk_libs:1.1.5"
}
```

## Translating

Please help us translate the app into several languages on [our translation platform](https://crowdin.com/project/WireGuard).
