# Installing Visual Studio Tools for Tizen

You need the following components on top of Visual Studio to make Visual Studio Tools for Tizen work:

- VSIX

  Visual Studio extension for Tizen packaging.

- Tizen Baseline SDK

  The SDK is shared with Tizen Studio, and it supports tools (such as Certificate Manager, Device Manager, Emulator, SDB, and on-demand rpm) for developing Tizen .NET applications.


## Prerequisites

To work with Visual Studio Tools for Tizen, your computer must have the following:

- At least 1.5 GB of available disk space.
- Visual Studio 2017 to use Tizen 4.0 and 5.0.
- Visual Studio 2019 to use Tizen 4.0 and 6.5.
- Visual Studio 2022 to use Tizen 4.0 and higher.
- The latest Tizen Tools updates support Tizen Native and Web app creation and are provided with Tizen Studio version 4.5 and above. Make sure the same is installed or [updated](../tizen-studio/setup/update-sdk.md) through Tizen package manager.
- Make sure to set the Tool Path (Tizen SDK) in **Tools > Options > Tizen > Tools** with installed Tizen Studio path. Also, ensure to set the Google Chrome Path for Tizen Web App Debugging support.
  
  Visual Studio Tools for Tizen works with all Visual Studio variations, including Community. Installing or re-installing Visual Studio with .NET desktop development, .NET Core cross-platform development, and desktop development with C++ toolsets is recommended.

  ![Visual Studio prerequisites](media/prerequisite-vs.png)
  ![Visual Studio prerequisites](media/prerequisite-vs-native.png)

- Java Development Kit (JDK)

  You must install Oracle Java Development Kit (JDK) 8 or OpenJDK 12 to use 
Tizen Baseline SDK. Make sure you download and install the exact version.

  - [Oracle Java Development Kit(JDK) 8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

  - OpenJDK 12 and OpenJFX: [OpenJDK 12 and OpenJFX Installation Guide](../tizen-studio/setup/openjdk.md#install-openjdk-for-windows).

### Emulator requirements

Tizen Emulator for Visual Studio has the same requirements as the emulator in Tizen Studio. To check the detailed hardware and software requirements for Tizen Emulator, see [Emulator Requirements](../tizen-studio/setup/prerequisites.md#emulator).

### Option 1

- Intel&reg; Hardware Acceleration Execution Manager (Intel&reg; HAXM) speeds up the Tizen emulation on Intel-VT-enabled systems. The Intel&reg; HAXM installation is started automatically as part of Visual Studio Tools for Tizen installation. For more information, see [Hardware Accelerated Execution Manager](../tizen-studio/setup/hardware-accelerated-execution-manager.md).

> [!NOTE]
> This option will not be applicable to and will not work on AMD processors.

- Make sure **Hyper-V** is disabled (in Windows 10 or higher):
  1. Input **Control Panel** on the **Search** box in Windows 10.

  2. Click **Control Panel > Programs and Features > Turn Windows features on or off**.

  3. Disable **Hyper-V** and click **OK**.

     Additional note: make sure **Virtual Machine Platform** should be disabled as well to use HAXM.

     ![Disable Hyper-V](media/cs_prerequisite-disable-hyperv.png)

  4. Reboot the computer.

### Option 2

- Microsoft's Hyper-V and the Windows Hypervisor Platform (WHPX). Hyper-V is a virtualization feature of Windows that makes it possible to run virtualized computer systems on a physical host computer.

- Make sure **Hyper-V** is enabled (PowerShell in Windows 10 or higher):
  1. Check the configuration

     > Get-WindowsOptionalFeature -FeatureName Microsoft-Hyper-V-All -Online

     FeatureName      : Microsoft-Hyper-V-All\
     DisplayName      : Hyper-V\
     Description      : Provides services and management tools for creating and running virtual machines and their resources.\
                      RestartRequired  : Possible\
                      State            : Disabled\
                      CustomProperties :

  2. Enable Hyper-V & HypervisorPlatform

     > Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All\
     > Enable-WindowsOptionalFeature -Online -FeatureName HypervisorPlatform -All

     ![Enable Hyper-V](media/cs_prerequisite-enable-hyperv.png)

  3. Reboot the computer.

<a name="install"></a>
## Visual Studio Tools for Tizen installation

To use Tizen SDK tools, you must install Visual Studio Tools for Tizen extension and Baseline SDK.

> [!NOTE] 
> If Tizen Studio is already installed on your computer, simply [set Tizen Baseline SDK path](#set-tizen-baseline-sdk) to the existing SDK instead of reinstalling it.


### Install the extension

Visual Studio Tools for Tizen extension is registered in the Visual Studio Marketplace. You can install extensions from the Visual Studio Marketplace in the Visual Studio IDE:

1. In the Visual Studio IDE menu, go to **Tools &gt; Extensions and Updates**.
2. In the Visual Studio Marketplace, search for **Tizen**.

   ![Marketplace](media/cps-extensions-and-updates.png)

3. Click **Download** and close the Visual Studio IDE.

   The installation starts.


### Install Tizen Baseline SDK

After installing Visual Studio Tools for Tizen extension, you must set up Tizen Baseline SDK in the following ways:

1. In the Visual Studio IDE menu, go to **Tools &gt; Tizen &gt; Tizen Package Manager**.
2. Select **Install new Tizen SDK**.

   ![Select new installation](media/howtoinstall-installwizard1.png)

3. Read the license document and click **I Agree**.

   ![Agree to license details](media/howtoinstall-installwizard2.png)

4. Enter the root directory path where you want to install and click **Next**.

   ![Set the installation path](media/howtoinstall-installwizard3.png)

5. Tizen SDK installer is downloaded and the baseline SDK is installed automatically.

   ![Installer download](media/howtoinstall-installwizard4.png)

   ![Baseline SDK installation](media/howtoinstall-installwizard5.png)

6. Finally, Tizen Package Manager installs Tizen SDK tools.

   ![Tool installation](media/howtoinstall-installwizard6.png)

<a name="set-tizen-baseline-sdk"></a>
### Set Tizen Baseline SDK path 

> [!NOTE]
> If you downloaded Visual Studio Tools for Tizen extension from the Visual Studio Marketplace and installed it on your computer, skip this step.


You can use Tizen Package Manager to set up Tizen Baseline SDK path or each tool path directly:

- To set up Tizen Baseline SDK path, refer to the following steps:
  1. In the Visual Studio IDE menu, go to **Tools &gt; Tizen &gt; Tizen Package Manager**.
  2. Select **Use installed Tizen SDK**.

     ![Baseline SDK Install](media/howtoinstall-baselineinstall5.png)

  3. Enter the root directory of your existing Tizen Studio installation.
     
     ![Baseline SDK Install](media/howtoinstall-baselineinstall6.png)

  > [!NOTE] 
  > If the installer gives a warning about your Tizen Studio version being too low, update Tizen Studio by using Tizen Package Manager after setting the tool path.

- To set up each tool path directly, follow the steps below: 
  1. In the Visual Studio IDE menu, go to **Tools &gt; Options &gt; Tizen &gt; Tools**.
  2. Enter the root directory of your existing Tizen Studio installation in the **Tool Path** field.
     ![Check the SDK tool path](media/howtoinstall-checktoolpath.png)

     The other tools paths are automatically set up.

### Install Emulator images

If you do not have a real device, you can run applications in Tizen Emulator.

To download emulator images, you can use Tizen Package Manager or Tizen Emulator Manager:

- To use Tizen Package Manager, follow the steps below:
  1. In the Visual Studio IDE menu, go to **Tools &gt; Tizen &gt; Tizen Package Manager**.
  2. Select the profiles and versions you want to install and click **Install**.

     ![Package Manager](media/howtoinstall-packagemanager.png)

- To use Tizen Emulator Manager, follow the steps below:

  > [!NOTE] 
  > Tizen Emulator Manager shows the emulator images installation window only when no images are installed on your computer.

  1. In the Visual Studio IDE menu, go to **Tools &gt; Tizen &gt; Tizen Emulator Manager**.
  2. Select the profiles and versions you want to install and click **OK**.

     ![Emulator Manager](media/howtoinstall-emulatormanager.png)


## Troubleshoot

If you encounter problems with the installation, refer to the following steps:

- To check whether VSIX is installed correctly, check Visual Studio Tools for Tizen properties by selecting **Tools &gt; Extensions and Updates** and searching for "Tizen".

  ![Check VSIX](media/cps-extensions-and-updates.png)

- To make sure Baseline Tizen SDK is installed correctly, check the tool path by selecting **Tools &gt; Options &gt; Tizen &gt; Tools**.

  ![Check the SDK tool path](media/howtoinstall-checktoolpath.png)

- To check whether Tizen Project properties have been copied correctly, make sure that the `Tizen.NET.ProjectType.props` and `Tizen.NET.ProjectType.targets` files are located in the `C:\Program Files (x86)\Microsoft Visual Studio\2017\Professional\MSBuild\Tizen\VisualStudio` folder.

  ![Project Property](media/cps-project-property.png)

