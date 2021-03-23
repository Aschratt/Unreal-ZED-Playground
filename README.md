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

### ZED SDK

In order for the project to work, you need the ZED SDK 3.1.2 to be installed. The SDK is the latest one that is currently supported by the [Stereolabs PlugIn](https://github.com/stereolabs/zed-unreal-plugin). It depends on [CUDA 10.2](https://developer.nvidia.com/cuda-10.2-download-archive), which also needs to be installed on the system. Note that there may be problems, if multiple versions of CUDA are installed in parallel.

### Patching Unreal Engine to build with VS 2019 and latest Windows 10 SDK

Start by cloning the UE4 ZED fork.

```shell
git clone --branch 4.21-zed https://github.com/Stereolabs-Unreal/UnrealEngine.git .
```

Next, download and copy the contents from the *patch* folder from this repository into the UE4 directory. If there are conflics, replace the existing files. Then apply the *vs2019.patch*.

```shell
git apply vs2019.patch
```

Finally, continue by running `Setup.bat` and `GenerateProjectFiles.bat`, as described in the [ZED documentation](https://www.stereolabs.com/docs/unreal/engine-setup/). Build the project in order to compile your custom UE4.21 distribution.

## Setup

Creating the project is actually pretty straightforward. Start by cloning the repository:

```shell
git clone --recurse-submodules https://github.com/Aschratt/Unreal-ZED-Playground.git .
```

Right click the *ZedPlayground.uproject* file and select "Switch Unreal Engine version...". Select your custom source build. Then right click the project again and select *Generate Visual Studio project files*.

**Important:** If you are using Visual Studio 2019, opening the solution will ask you to update the Toolset and Windows SDK version. Select *Don't update* on both before you continue! If you did hit update by mistake, try re-generating the project files.

When launching the *ZedPlayground* application, make sure you've selected the build configuration used for building the engine with (e.g. Development_Editor/Win64).