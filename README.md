# Unreal Engine 4 playground for ZED (mini)

Playing around with the ZED mini in Unreal Engine 4.

## Prerequisites

Before this project can be built, the ZED fork for [UE4.21](https://github.com/Stereolabs-Unreal/UnrealEngine/tree/4.21-zed) needs to be built. Unfortunately, the fork has never been pulled into UE4 and thus the latest version that is supported is 4.21. The version does have some issues and needs some manual fixes to be applied when used with Windows 10 and Visual Studio 2019. 

### Required Visual Studio packages

Before starting, launch up the Visual Studio installer and make sure you've installed the following components.

#### Visual Studio 2019

Workloads:
- Desktop Development with C++

Individual Components
- Windows 10 SDK v10.0.17134.0
- MSVC v141 - VS 2017 C++ x64/x86 Buildtools (v14.16)

#### Visual Studio 2017

**Optional**, if you are *not* creating new projects (e.g. by simply using this project inside VS 2019), you can skip installing the VS 2017 IDE. However, the Unreal Editor will look for the IDE on your system and disable the project generation, if it is not installed.

Workloads:
- Desktop Development with C++

### Patching Unreal Engine to build with VS 2019 and latest Windows 10 SDK

Start by cloning the UE4 ZED fork.

```shell
git clone --branch 4.21-zed https://github.com/Stereolabs-Unreal/UnrealEngine.git .
```

Next, download and copy the contents from the *patch* folder from this repository into the UE4 directory. If there are conflics, replace the existing files. Then apply the *vs2019.patch*.

```shell
git apply vs2019.patch
```

Finally, continue by running `Setup.bat` and `GenerateProjectFiles.bat`, as described in the [ZED documentation](https://www.stereolabs.com/docs/unreal/engine-setup/).
