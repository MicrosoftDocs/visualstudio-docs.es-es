---
title: Migrate apps to the Universal Windows Platform (UWP) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5279ab9b-71d9-4be5-81f6-a1f24b06f5fb
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5794aa5ab7dc14932c65a9156ea9252e71731155
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299475"
---
# <a name="migrate-apps-to-the-universal-windows-platform-uwp"></a>Migrar aplicaciones a la Plataforma universal de Windows (UWP)
Haga los cambios manuales necesarios en los archivos de proyecto existentes para las aplicaciones de la Tienda Windows 8.1, las aplicaciones de Windows Phone 8.1 o las aplicaciones universales de Windows creadas con Visual Studio 2015 RC, de modo que se puedan usar con Visual Studio 2015 RTM. (Si tiene una aplicación universal para Windows 8.1 con un proyecto de aplicación de Windows y un proyecto de Windows Phone, deberá seguir los pasos indicados a continuación para migrar cada proyecto).

 Con la Plataforma universal de Windows ahora puede dirigir su aplicación a una o varias familias de dispositivos. Si desea obtener más información sobre las aplicaciones universales de Windows, vea esta [guía de la plataforma](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx).

- [Migrar las aplicaciones existentes de Windows Phone 8.1 o la Tienda Windows 8.1 C#/VB](#MigrateCSharp) para usar la plataforma universal de Windows.

- [Migrar las aplicaciones existentes de Windows Phone 8.1 o la Tienda Windows 8.1 C++](#MigrateCPlusPlus) para usar la plataforma universal de Windows.

- [Cambios necesarios para las aplicaciones universales de Windows existentes creadas con Visual Studio 2015 RC](#PreviousVersions).

- [Cambios necesarios para los proyectos de prueba unitaria existentes de las aplicaciones universales de Windows creadas con Visual Studio 2015 RC](#MigrateUnitTest).

  Si no desea hacer todos estos cambios, obtenga información sobre cómo [migrar sus aplicaciones existentes](https://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) a un nuevo proyecto universal de Windows.

## <a name="MigrateCSharp"></a> Migrate your C#/VB Windows Store 8.1 or Windows Phone 8.1 apps to use the Universal Windows Platform

#### <a name="migrate-your-cvb-project-files"></a>Migrar los archivos de proyecto de C#/VB

1. Para averiguar la plataforma universal de Windows que ha instalado, abra esta carpeta: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Contiene una lista de carpetas para cada plataforma universal de Windows que está instalada. El nombre de la carpeta es la versión de la plataforma universal de Windows que ha instalado. Por ejemplo, este dispositivo Windows 10 tiene la versión 10.0.10240.0 de la Plataforma universal de Windows instalada.

     ![Open the folder to view the versions installed](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Se puede instalar más de una versión de la plataforma universal de Windows. Se recomienda usar la versión más reciente de la aplicación.

2. Con el Explorador de archivos, vaya a la carpeta en la que está almacenado su proyecto UWP. Cree un archivo .json en esta carpeta. Asigne el nombre project.json al archivo y agréguele el siguiente contenido:

    ```json
    {
      "dependencies": {
        "Microsoft.ApplicationInsights": "1.0.0",
        "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",
        "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",
        "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"
      },
      "frameworks": {
        "uap10.0": {}
      },
      "runtimes": {
        "win10-arm": {},
        "win10-arm-aot": {},
        "win10-x86": {},
        "win10-x86-aot": {},
        "win10-x64": {},
        "win10-x64-aot": {}
      }
    }

    ```

3. Cree un archivo llamado default.rd.xml con el siguiente contenido. Si tiene un proyecto de VB, agregue este archivo al directorio My Project para el proyecto. Si tiene un proyecto de C#, agregue este archivo al directorio Properties para el proyecto.

    ```xml
    <?xml version="1.0"?>
    <!-- This file contains Runtime Directives used by .NET Native. The defaults here are suitable for most developers. However, you can modify these parameters to modify the behavior of the .NET Native optimizer. Runtime Directives are documented at http://go.microsoft.com/fwlink/?LinkID=391919 To fully enable reflection for App1.MyClass and all of its public/private members <Type Name="App1.MyClass" Dynamic="Required All"/> To enable dynamic creation of the specific instantiation of AppClass<T> over System.Int32 <TypeInstantiation Name="App1.AppClass" Arguments="System.Int32" Activate="Required Public" /> Using the Namespace directive to apply reflection policy to all the types in a particular namespace <Namespace Name="DataClasses.ViewModels" Seralize="All" /> -->
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata"><Application>
    <!-- An Assembly element with Name="*Application*" applies to all assemblies in the application package. The asterisks are not wildcards. -->
    <Assembly Dynamic="Required All" Name="*Application*"/>
    <!-- Add your application specific runtime directives here. -->
    </Application></Directives>
    ```

4. Abra la solución que contiene su aplicación existente de Windows Phone 8.1 o la Tienda Windows 8.1 en Visual Studio.

5. En el Explorador de soluciones, haga clic con el botón secundario en el proyecto existente de la aplicación y, luego, seleccione **Descargar el proyecto**. Después de descargar el proyecto, haga clic en el archivo de proyecto nuevo y elija Editar el archivo .csproj o .vbproj.

     ![Right click the project and choose Edit](../misc/media/uap-editproject.png "UAP_EditProject")

6. Find the \<PropertyGroup> element that contains the \<TargetPlatformVersion> element with a value of 8.1. Do the following steps for this \<PropertyGroup> element:

    1. Set the value of the \<Platform> element to: **x86**.

    2. Add a \<TargetPlatformIdentifier> element and set its value to: **UAP**.

    3. Change the existing value of the \<TargetPlatformVersion> element to be the value of the Universal Windows Platform version that you installed. Also add a \<TargetPlatformMinVersion> element and give it the same value.

    4. Change the value of the \<MinimumVisualStudioVersion> element to: **14**.

    5. Replace the \<ProjectTypeGuids> element as shown below:

         Para C#:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
        ```

         Para VB:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>
        ```

    6. Add an \<EnableDotNetNativeCompatibleProfile> element and set its value to: **true**.

    7. La escala de activos predeterminada para las aplicaciones universales de Windows es de 200. If your project includes assets not scaled at 200, you will need to add a \<UapDefaultAssetScale> element with the value of the scale of your assets to this PropertyGroup. Más información sobre [activos y escalas](https://msdn.microsoft.com/library/jj679352.aspx).

         Now your \<PropertyGroup> element should look similar to this example:

        ```xml
        <PropertyGroup>
            …
             <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
             <TargetPlatformVersion>10.0.10240.0</TargetPlatformVersion>
             <TargetPlatformMinVersion>10.0.10240.0</TargetPlatformMinVersion>
             <TargetPlatformIdentifier>UAP</TargetPlatformIdentifier>
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>
             <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
             <UapDefaultAssetScale>100</UapDefaultAssetScale>
             …
        </PropertyGroup>
        ```

7. Reemplace todas las instancias de 12.0 por 14.0 para que reflejen la versión de Visual Studio que está usando ahora. Como estas instancias:

    ```xml
    <Project Tools Version="14.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

    ```
    <PropertyGroup Condition=" '$(VisualStudioVersion)' == '' or '$(VisualStudioVersion)' < '14.0' ">
        <VisualStudioVersion>14.0</VisualStudioVersion>
    ```

8. Find \<PropertyGroup> elements that are configured for the AnyCPU platform as part of the Condition attribute. Quite estos elementos y todos sus elementos secundarios. AnyCPU no es compatible con las aplicaciones de Windows 10 en Visual Studio 2015. For example, you should remove \<PropertyGroup> elements like these ones:

    ```xml
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <PlatformTarget>AnyCPU</PlatformTarget>
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <PlatformTarget>AnyCPU</PlatformTarget>
        <DebugType>pdbonly</DebugType>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
    ```

9. For each remaining \<PropertyGroup> element, check if the element has a Condition attribute with a Release configuration. If it does, but it does not contain a \<UseDotNetNativeToolchain> element, then add one. Set the value for the \<UseDotNetNativeToolchain> element to true, like this:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|x64'">
        <OutputPath>bin\x64\Release\</OutputPath>
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <Optimize>true</Optimize>
        <NoWarn>;2008</NoWarn>
        <DebugType>pdbonly</DebugType>
        <PlatformTarget>x64</PlatformTarget>
        <UseVSHostingProcess>false</UseVSHostingProcess>
        <ErrorReport>prompt</ErrorReport>
        <Prefer32Bit>true</Prefer32Bit>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>
    ```

10. For Windows Phone projects only, remove the \<PropertyGroup> element that contains a \<TargetPlatformIdentifier> element with a value of WindowsPhoneApp. Asimismo quite los elementos secundarios de este elemento:

    ```xml
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' ">
      <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier>
    </PropertyGroup>
    ```

11. Find the \<ItemGroup> element that contains the \<AppxManifest> element. Add the following \<None> element as a child of the \<ItemGroup> element:

    ```xml
    <None Include="project.json" />
    ```

12. Find the \<ItemGroup> element that contains other assets that are added to your project such as logo .png files (\<Content Include="Assets\Logo.scale-100.png" />). Add the following \<Content> child element to this \<ItemGroup> element:

     **For C#:**

    ```xml
    <Content Include="Properties\default.rd.xml" />
    ```

     **For VB:**

    ```xml
    <Content Include="My Project\default.rd.xml" />
    ```

13. Find the \<ItemGroup> element that includes \<Reference> children elements to NuGet packages. Tome nota de los paquetes de NuGet empleados porque deberá descargarlos con el Administrador de paquetes de NuGet cuando se haya vuelto a cargar el proyecto. Remove this \<ItemGroup> along with its children. Por ejemplo, un proyecto UWP podría tener los siguientes paquetes de NuGet que deben quitarse:

    ```xml
    <ItemGroup>
        <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>
          <Private>True</Private>
        </Reference>
      </ItemGroup>
    ```

14. Guarde los cambios.

15. Cierre el archivo .csproj o .vbproj.

16. Haga clic con el botón secundario en el proyecto en el Explorador de soluciones y elija Volver a cargar el proyecto en el menú contextual. Todos los archivos del proyecto ahora deben aparecer en el Explorador de soluciones.

17. Use el Administrador de NuGet para volver a agregar los paquetes que eliminó en un paso anterior.

     Ahora tiene que seguir los pasos necesarios para [actualizar los archivos de manifiesto del paquete](#PackageManifest) de todos los proyectos de la Tienda Windows 8.1 o de Windows Phone 8.1.

## <a name="MigrateCPlusPlus"></a> Migrate your C++ Windows Store 8.1 or Windows Phone 8.1 apps to use the Universal Windows Platform

#### <a name="migrate-your-c-project-files"></a>Migrar los archivos de proyecto de C++

1. Para averiguar la plataforma universal de Windows que ha instalado, abra esta carpeta: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Contiene una lista de carpetas para cada plataforma universal de Windows que está instalada. El nombre de la carpeta es la versión de la plataforma universal de Windows que ha instalado. Por ejemplo, este dispositivo Windows 10 tiene la versión 10.0.10240.0 de la Plataforma universal de Windows instalada.

     ![Open the folder to view the versions installed](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Se puede instalar más de una versión de la plataforma universal de Windows. Se recomienda usar la versión más reciente de la aplicación.

2. Abra la solución que contiene su aplicación existente de Windows Phone 8.1 o la Tienda Windows 8.1 C++ en Visual Studio.

     Haga clic con el botón secundario en el proyecto existente en el Explorador de soluciones y, a continuación, seleccione **Descargar el proyecto**. Después de descargar el proyecto, vuelva a hacer clic con el botón secundario en el archivo de proyecto y elija Editar el archivo .vbproj.

     ![Right&#45;click project file and choose to edit](../misc/media/uap-editcplusproject.png "UAP_EditCPlusProject")

3. Find the \<PropertyGroup> element that contains the \<ApplicationTypeRevision> element with a value of 8.1. Do the following steps for this \<PropertyGroup> element:

    1. Add a \<WindowsTargetPlatformVersion> element and a \<WindowsTargetPlatformMinVersion> element and give them the value of the Universal Windows Platform version that you installed.

    2. Actualice el valor del elemento ApplicationTypeRevision de 8.1 a 10.0.

    3. Change the value of the \<MinimumVisualStudioVersion> element to: 14.

    4. Add an \<EnableDotNetNativeCompatibleProfile> element and set its value to: true.

    5. La escala de activos predeterminada para las aplicaciones universales de Windows es de 200. If your project includes assets not scaled at 200, you will need to add a \<UapDefaultAssetScale> element with the value of the scale of your assets to this PropertyGroup. Más información sobre [activos y escalas](https://msdn.microsoft.com/library/jj679352.aspx).

    6. For Windows Phone projects only, change the value of \<ApplicationType> from Windows Phone to Windows Store.

         Now your \<PropertyGroup> element should look similar to this example:

        ```xml
        <PropertyGroup>
            …
                  <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>
             <ApplicationType>Windows Store</ApplicationType>
             <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>
             <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
             <UapDefaultAssetScale>100</UapDefaultAssetScale>
             …
        </PropertyGroup>
        ```

4. Change all instances of the \<PlatformToolset> element to have the value v140. Por ejemplo:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>
    ```

5. For each remaining \<PropertyGroup> element, check if the element has a Condition attribute with a Release configuration. If it does, but it does not contain a \<UseDotNetNativeToolchain> element, then add one. Set the value for the \<UseDotNetNativeToolchain> element to true, like this:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|X64'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

6. Guarde los cambios. Después cierre el archivo de proyecto.

7. Haga clic con el botón secundario en el archivo de proyecto en el Explorador de soluciones y elija Volver a cargar el proyecto en el menú contextual. Todos los archivos del proyecto ahora deben aparecer en el Explorador de soluciones.

     Ahora tiene que seguir los pasos necesarios para [actualizar los archivos de manifiesto del paquete](#PackageManifest) de todos los proyectos de la Tienda Windows 8.1 o de Windows Phone 8.1.

## <a name="PackageManifest"></a> Update your package manifest file for all your Windows Store 8.1 or Windows Phone 8.1 projects
 Debe actualizar el archivo de manifiesto del paquete para cada proyecto de la solución.

#### <a name="update-your-package-manifest-file"></a>Actualizar el archivo de manifiesto del paquete

1. Abra el archivo package.appxmanifest en el proyecto. Debe editar el archivo Package.AppxManifest para cada uno de los proyectos de la Tienda Windows y Windows Phone.

2. You need to update the \<Package> element with the new schemas based on your existing project type. Primero quite los esquemas siguientes en función de si tiene un proyecto de Windows Phone o la Tienda Windows.

    **OLD for Windows Store project:** Your \<Package> element will look similar to this one.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
       xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">

   ```

    **OLD for Windows Phone project:** Your \<Package> element will look similar to this one.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
   xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest"
   xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest"
   xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">
   ```

    **NEW for Universal Windows Platform:** Add the schemas below to your \<Package> element. Quite todos los prefijos de identificador de espacio de nombres asociados de los elementos para los esquemas que acaba de quitar. Actualice la propiedad IgnorableNamespaces a: uap mp. Your new \<Package> element should look similar to this one.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
       xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
       xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
      IgnorableNamespaces= "uap mp">

   ```

3. Add a \<Dependencies> child element to the \<Package> element. Then add a \<TargetDeviceFamily> child element to this \<Dependencies> element with Name, MinVersion, and MaxVersionTested attributes. Asigne al atributo Name el valor: Windows.Universal. Asigne a los atributos MinVersion y MaxVersionTested el valor de la versión de plataforma universal de Windows que tenga instalada. Este elemento debe ser similar a este.

   ```xml
   <Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" />
   </Dependencies>
   ```

4. **For Windows Store only:** You need to add a \<mp:PhoneIdentity> child element to the \<Package> element. Agregue un atributo PhoneProductId y un atributo PhonePublisherId. Set the PhoneProductId to have the same value as the Name attribute in the \<Identity> element. Establezca el valor de PhonePublishedId en: 00000000-0000-0000-0000-000000000000. Así:

   ```xml
   <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" />
   <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>
   ```

5. Find the \<Prerequisites> element and delete this element and any child elements that it has.

6. Add the **uap** namespace to the following \<Resource> elements: Scale, DXFeatureLevel. Por ejemplo:

   ```xml
   <Resources>
     <Resource Language="en-us"/>
    <Resource uap:Scale="180"/>
    <Resource uap:DXFeatureLevel="dx11"/>
   </Resources>

   ```

7. Add the **uap** namespace to the following \<Capability> elements: documentsLibrary, picturesLibrary, videosLibrary, musicLibrary, enterpriseAuthentication, sharedUserCertificates, removableStorage, appointments, and contacts. Por ejemplo:

   ```xml
   <Capabilities>
     <uap:Capability Name="documentsLibrary"/>
     <uap:Capability Name="removableStorage"/>
   </Capabilities>

   ```

8. Add the **uap** namespace to the \<VisualElements> element and any of its child elements. Por ejemplo:

   ```xml
   <uap:VisualElements
       DisplayName="My WWA App"
       Square150x150Logo="images/150x150.png"
       Square44x44Logo="images/44x44.png"
       Description="My WWA App"
       BackgroundColor="#777777">
     <uap:SplashScreen Image="images/splash.png"/>
   </uap:VisualElements>

   ```

    **Solo se aplica a la Tienda Windows:** los nombres de tamaño de mosaico han cambiado. Change the attributes in the \<VisualElements> element to reflect the new converged tile sizes. 70 x 70 se convierte en 71 x 71, y 30 x 30 se convierte en 44 x 44.

    **ANTIGUO:** nombres de tamaño de mosaico

   ```xml
   <m2:VisualElements
       …
       Square30x30Logo="Assets\SmallLogo.png"
       …>
    <m2:DefaultTile
         …
         Square70x70Logo="images/70x70.png">
   </m2:VisualElements>

   ```

    **NUEVO:** nombres de tamaño de mosaico

   ```xml
   <uap:VisualElements
       …
       Square44x44Logo="Assets\SmallLogo.png"
       …>
    <uap:DefaultTile
         …
         Square71x71Logo="images/70x70.png">
   </uap:VisualElements>

   ```

9. Add the **uap** namespace to the \<ApplicationContentUriRules> and all its child elements. Por ejemplo:

    ```xml
    <uap:ApplicationContentUriRules>
      <uap:Rule Type="include" Match="https://www.microsoft.com/"/>
      <uap:Rule Type="exclude" Match="*.pdf"/>
    </uap:ApplicationContentUriRules>

    ```

10. Add the **uap** namespace to the following \<Extension> elements and all of its child elements: windows.accountPictureProvide,  windows.alarm, windows.appointmentsProvider windows.autoPlayContent,  windows.autoPlayDevice, windows.cachedFileUpdate, windows.cameraSettings, windows.fileOpenPicker, windows.fileTypeAssociation, windows.fileSavePicke, windows.lockScreenCall, windows.printTaskSettings, windows.protocol, windows.search, windows.shareTarget. Por ejemplo:

    ```xml
    <Extensions>
      <uap:Extension Category="windows.alarm"/>
      <uap:Extension Category="windows.search" EntryPoint="MyActivateableClassId.baz"/>
      <uap:Extension Category="windows.protocol">
        <uap:Protocol Name="mailto" DesiredView="useHalf">
         <uap:DisplayName>MailTo Protocol</uap:DisplayName>
        </uap:Protocol>
      </uap:Extension>
    </Extensions>

    ```

11. Agregue el espacio de nombres **uap** a las tareas en segundo plano de tipo chatMessageNotification. Por ejemplo:

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
     <BackgroundTasks ServerName="MyBackgroundTasks">
        <uap:Task Type="chatMessageNotification"/>
      </BackgroundTasks>
    </Extension>

    ```

12. Cambie las dependencias del marco. Add a Publisher name to all \<PackageDependency> elements, and specify a MinVersion if it’s not already specified.

     **OLD:** \<PackageDependency> element

    ```xml
    <Dependencies>
     <PackageDependency Name="Microsoft.VCLibs.120.00" />
    </Dependencies>

    ```

     **NEW:** \<PackageDependency> element

    ```xml
    <Dependencies>
     <PackageDependency
          Name="Microsoft.VCLibs.120.00"
          Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"
          MinVersion="12.0.30113.0" />
    </Dependencies>

    ```

     Use los valores adecuados de Publisher y MinVersion para el marco real que está usando. Tenga en cuenta que estos nombres pueden cambiar en Windows 10.

13. Reemplace las tareas de tipo segundo plano gattCharacteristicNotification y rfcommConnection por una tarea de tipo Bluetooth. Por ejemplo:

     **OLD:**

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
    <BackgroundTasks ServerName="MyBackgroundTasks">
                <Task Type="rfcommConnection"/>
               <Task Type="gattCharacteristicNotification"/>
    </BackgroundTasks>
    </Extension>
    ```

     **NUEVO:** con tarea de tipo Bluetooth.

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
    <BackgroundTasks ServerName="MyBackgroundTasks">
               <Task Type="bluetooth"/>
    </BackgroundTasks>
    </Extension>
    ```

14. Reemplace las funcionalidades del dispositivo Bluetooth bluetooth.rfcomm y bluetooth.genericAttributeProfile por una funcionalidad de Bluetooth genérica. Por ejemplo:

     **OLD:**

    ```xml
    <Capabilities>
      <m2:DeviceCapability Name="bluetooth.rfcomm">
        <m2:Device Id="any">
         <m2:Function Type="serviceId:34B1CF4D-1069-4AD6-89B6-E161D79BE4D8"/>
        </m2:Device>
      </m2:DeviceCapability>
      <m2:DeviceCapability Name="bluetooth.genericAttributeProfile">
        <m2:Device Id="any">
         <m2:Function Type="name:heartRate"/>
        </m2:Device>
      </m2:DeviceCapability>
    </Capabilities>
    ```

     **NUEVO:** reemplazado por una funcionalidad de Bluetooth genérica.

    ```xml
    <Capabilities>
      <uap:DeviceCapability Name="bluetooth"/>
    </Capabilities>

    ```

15. Quite todos los elementos en desuso.

    1. These attributes for \<VisualElements> are deprecated and should be removed:

       - The \<VisualElements> attributes: ForegroundText, ToastCapable

       - The \<DefaultTile> attribute DefaultSize

       - The \<ApplicationView> element

         Por ejemplo:

       ```xml
       <m2:VisualElements
           …
           ForegroundText="dark"
           ToastCapable="true">
       <m2:DefaultTile DefaultSize="square150x150Logo"/>
         <m2:ApplicationView MinWidth="width320"/>
       </m2:VisualElements>

       ```

    2. Quite las extensiones Windows.contact y windows.contactPicker y todos los elementos de estas extensiones.

16. Guarde el archivo Package.appxmanifest. Después cierre Visual Studio.

17. Deberá quitar algunos archivos ocultos para poder volver a abrir la solución.

    1. Abra el Explorador de archivos, haga clic en **Vista** en la barra de herramientas y seleccione **Elementos ocultos** y **Extensiones de nombre de archivo**. Open this folder on your machine: \<path for the location of your solution>\\.vs\\{Project Name}\v14. Si hay un archivo con una extensión de archivo .suo, elimínelo.

    2. Ahora vuelva a la carpeta donde se encuentra la solución. Abra las carpetas de los proyectos que existen en la solución. Si un archivo dentro de cualquiera de estas carpetas de proyecto tiene una extensión .csproj.user o .vbproj.user, elimínelo.

         Ahora puede volver a abrir la solución en Visual Studio. Está listo para codificar, compilar y depurar la aplicación con la plataforma universal de Windows.

         Aprenda a [adaptar el código](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) para sacar el máximo partido a las novedades de la Plataforma universal de Windows.

## <a name="PreviousVersions"></a> Changes required for existing Universal Windows apps created with Visual Studio 2015 RC
 Si creó aplicaciones universales de Windows 10 con Visual Studio 2015 RC, debe redirigir el proyecto para usar la versión de la Plataforma universal de Windows instalada con la versión más reciente de Visual Studio 2015. Las versiones anteriores no son compatibles. Los cambios necesarios son diferentes según el idioma utilizado para crear la aplicación:

- [C#/VB apps](#RCUpdate10CSharp)

- [C++ apps](#RCUpdate10CPlusPlus)

### <a name="RCUpdate10CSharp"></a> Update your C#/VB projects to use the latest Universal Windows Platform
 Al abrir la solución de la aplicación existente, verá que la aplicación necesita una actualización:

 ![View your project in Solution Explorer](../misc/media/uwp-updaterequired.png "UWP_UpdateRequired")

 Si decide volver a cargar este proyecto desde el Explorador de soluciones, verá este cuadro de diálogo:

 ![Retarget your app to use the correct SDK](../misc/media/missingsdkforuap.png "MissingSDKforUAP")

 Dado que el SDK de la plataforma universal de Windows para el proyecto no es compatible por el momento, no podrá instalarlo. Simplemente haga clic en Aceptar y siga estos pasos.

##### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a>Actualizar los proyectos C#/VB para que usen la plataforma universal de Windows más reciente

1. Para averiguar la plataforma universal de Windows que ha instalado, abra esta carpeta: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Contiene una lista de carpetas para cada plataforma universal de Windows que está instalada. El nombre de la carpeta es la versión de la plataforma universal de Windows que ha instalado. Por ejemplo, este dispositivo Windows 10 tiene la versión 10.0.10240.0 de la Plataforma universal de Windows instalada.

    ![Open the folder to view the versions installed](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

    Se puede instalar más de una versión de la plataforma universal de Windows. Se recomienda usar la versión más reciente de la aplicación.

2. Con el Explorador de archivos, vaya a la carpeta en la que está almacenado su proyecto UWP. Elimine el archivo packages.config y cree un nuevo archivo .json en esta carpeta. Asigne el nombre project.json al archivo y agréguele el siguiente contenido:

   ```json

   {
     "dependencies": {
       "Microsoft.ApplicationInsights": "1.0.0",
       "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",
       "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",
       "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"
     },
     "frameworks": {
       "uap10.0": {}
     },
     "runtimes": {
       "win10-arm": {},
       "win10-arm-aot": {},
       "win10-x86": {},
       "win10-x86-aot": {},
       "win10-x64": {},
       "win10-x64-aot": {}
     }
   }

   ```

3. Con Visual Studio, abra la solución que contiene la aplicación universal de Windows de C#/VB. Verá que el archivo de proyecto (archivo .csproj o .vbproj) debe actualizarse. Haga clic con el botón secundario en el archivo del proyecto y elija editar el archivo.

    ![Right click the project and choose Edit](../misc/media/uap-editproject.png "UAP_EditProject")

4. Find the \<PropertyGroup> element that contains the \<TargetPlatformVersion> and \<TargetPlatformMinVersion> elements. Change the existing value of the \<TargetPlatformVersion> and \<TargetPlatformMinVersion> elements to be the same version of the Universal Windows Platform that you have installed.

    La escala de activos predeterminada para las aplicaciones universales de Windows es de 200. Projects created with Visual Studio 2015 RC included assets scaled at 100, you will need to add a \<UapDefaultAssetScale> element with a value of 100 to this PropertyGroup. Más información sobre [activos y escalas](https://msdn.microsoft.com/library/jj679352.aspx).

5. Si agregó referencias a los SDK de extensión de UWP (por ejemplo, el SDK de Windows Mobile), deberá actualizar la versión del SDK. For example this \<SDKReference> element:

   ```xml
   <SDKReference Include="WindowsMobile, Version=10.0.0.1">
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>
   </SDKReference>

   ```

    Debe cambiarse por el siguiente:

   ```xml
   <SDKReference Include="WindowsMobile, Version=10.0.10240.0">
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>
   </SDKReference>

   ```

6. Find the \<Target> element with a name attribute that has the value: EnsureNuGetPackageBuildImports. Elimine este elemento y todos sus elementos secundarios.

   ```xml
   <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">
       <PropertyGroup>
         <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>
       </PropertyGroup>
       <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" />
       <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" />
   </Target>
   ```

7. Find and delete the \<Import> elements with Project and Condition attributes that reference Microsoft.Diagnostics.Tracing.EventSource and Microsoft.ApplicationInsights, like this:

   ```xml
   <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" />
   <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />

   ```

8. Find the \<ItemGroup> that has \<Reference> children elements to NuGet packages. Tome nota de los paquetes de NuGet referenciados, ya que necesitará esta información para un paso posterior. Una diferencia significativa del formato de proyecto de Windows 10 entre Visual Studio 2015 RC y Visual Studio 2015 RTM es que el formato RTM usa [NuGet](https://docs.microsoft.com/nuget/) versión 3.

    Remove the \<ItemGroup> and all its children. Por ejemplo, un proyecto UWP creado con Visual Studio RC tendrá los siguientes paquetes de NuGet que se deben quitar:

   ```xml
   <ItemGroup>
       <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>
         <Private>True</Private>
       </Reference>
     </ItemGroup>

   ```

9. Find the \<ItemGroup> element that contains an \<AppxManifest> element. If there is a \<None> element with an Include attribute set to: packages.config, delete it. Also, add a \<None> element with an Include attribute and set its value to: project.json.

10. Guarde los cambios. Después cierre el archivo de proyecto.

11. Haga clic con el botón secundario en el archivo de proyecto en el Explorador de soluciones y elija Volver a cargar el proyecto en el menú contextual. Todos los archivos del proyecto ahora deben aparecer en el Explorador de soluciones.

12. Seleccione el archivo ApplicationInsights.config en el Explorador de soluciones y abra sus propiedades. Establezca la propiedad Acción de compilación en "Contenido" y la propiedad Copiar en el directorio de salida en "Copiar si es posterior".

13. Abra el archivo package.appxmanifest en el proyecto.

    1. Find the \<TargetDeviceFamily> element. Cambie los atributos MinVersion y MaxVersionTested para que correspondan con la versión de Plataforma universal de Windows que tenga instalada. Así:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Guarde los cambios.

14. Use el Administrador de NuGet para agregar los paquetes que eliminó en el paso anterior. Una diferencia significativa del formato de proyecto de Windows 10 entre Visual Studio 2015 RC y Visual Studio 2015 RTM es que el formato RTM usa [NuGet](https://docs.microsoft.com/nuget/) versión 3.

    Ahora puede codificar, compilar y depurar la aplicación.

    Si tiene proyectos de prueba unitaria para sus aplicaciones universales de Windows, también debe seguir [estos pasos](#MigrateUnitTest).

### <a name="RCUpdate10CPlusPlus"></a> Update your C++ projects to use the latest Universal Windows Platform

1. Para averiguar la plataforma universal de Windows que ha instalado, abra esta carpeta: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Contiene una lista de carpetas para cada plataforma universal de Windows que está instalada. El nombre de la carpeta es la versión de la plataforma universal de Windows que ha instalado. Por ejemplo, este dispositivo Windows 10 tiene la versión 10.0.10240.0 de la Plataforma universal de Windows instalada.

     ![Open the folder to view the versions installed](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Se puede instalar más de una versión de la plataforma universal de Windows. Se recomienda usar la versión más reciente de la aplicación.

2. Abra la solución que contiene la aplicación universal de Windows de C++. Haga clic con el botón secundario en el archivo .vcxproj del proyecto y elija descargar el archivo de proyecto. Después de descargar el proyecto, vuelva a hacer clic con el botón secundario en el archivo de proyecto y elija editarlo.

     ![Unload the project, then edit the project file](../misc/media/uap-editearliercplus.png "UAP_EditEarlierCPlus")

3. Find any \<PropertyGroup> elements that do not contain a Condition attribute but do contain an \<ApplicationTypeRevision> element. Actualice el valor ApplicationTypeRevision de 8.2 a 10.0. Add a \<WindowsTargetPlatformVersion> and a \<WindowsTargetPlatformMinVersion> element and set their values to be the value of the Universal Windows Platform version that you installed.

     Add an \<EnableDotNetNativeCompatibleProfile> element and set its value to true if the element does not already exist.

     La escala de activos predeterminada para las aplicaciones universales de Windows es de 200. Projects created with Visual Studio 2015 RC included assets scaled at 100, you will need to add a \<UapDefaultAssetScale> element with a value of 100 to this PropertyGroup. Más información sobre [activos y escalas](https://msdn.microsoft.com/library/jj679352.aspx).

     So this \<PropertyGroup> element will now be similar to this:

    ```xml
    <PropertyGroup Label="Globals">
        …
        <MinimumVisualStudioVersion>14.0</MinimumVisualStudioVersion>
        <ApplicationType>Windows Store</ApplicationType>
        <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
        <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
        <UapDefaultAssetScale>100</UapDefaultAssetScale>
      </PropertyGroup>

    ```

4. For each remaining \<PropertyGroup> element, check if the element has a Condition attribute with a Release configuration. If it does, but it does not contain a \<UseDotNetNativeToolchain> element, then add one. Set the value for the \<UseDotNetNativeToolchain> element to true, like this:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

5. You need to update the \<EnableDotNetNativeCompatibleProfile> element and the \<UseDotNetNativeToolchain> element to enable .NET Native, but .NET Native is not enabled in the C++ templates.

     Guarde los cambios. Después cierre el archivo de proyecto.

6. Haga clic con el botón secundario en el archivo de proyecto en el Explorador de soluciones y elija Volver a cargar el proyecto en el menú contextual. Todos los archivos del proyecto ahora deben aparecer en el Explorador de soluciones.

7. Abra el archivo package.appxmanifest en el proyecto.

    1. Find the \<TargetDeviceFamily> element. Cambie los atributos MinVersion y MaxVersionTested para que correspondan con la versión de Plataforma universal de Windows que tenga instalada. Así:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Guarde los cambios.

         Ahora puede codificar, compilar y depurar la aplicación.

         Si tiene proyectos de prueba unitaria para sus aplicaciones universales de Windows, también debe seguir [estos pasos](#MigrateUnitTest).

## <a name="MigrateUnitTest"></a> Changes required for existing unit test projects for Universal Windows apps created with Visual Studio 2015 RC
 Si creó proyectos de prueba unitaria para aplicaciones universales de Windows 10 con Visual Studio 2015 RC, debe hacer estos cambios adicionales en los archivos de proyecto para usar dichos proyectos de prueba con la versión más reciente de Visual Studio 2015. Los cambios necesarios son diferentes según el idioma utilizado para crear la aplicación:

- [C#/VB apps](#UnitTestRCUpdate10CSharp)

- [C++ apps](#UnitTestRCUpdate10CPlusPlus)

### <a name="UnitTestRCUpdate10CSharp"></a> Update your C#/VB unit test projects

1. Con Visual Studio, abra la solución que contiene el proyecto de prueba unitaria de C#/VB. Change the value of the \<OuttputType> element to: AppContainerExe.

   ```xml

   <OutputType>AppContainerExe</OutputType>

   ```

2. Replace this element \<EnableCoreRuntime>false\</EnableCoreRuntime> with the following element:

   ```xml

   <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>

   ```

3. Quite las siguientes líneas:

   ```xml

   <PropertyGroup>
       <AppXPackage>True</AppXPackage>
       <AppxPackageIncludePrivateSymbols>true</AppxPackageIncludePrivateSymbols>
    </PropertyGroup>
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
    <PlatformTarget>AnyCPU</PlatformTarget>
    <DebugSymbols>true</DebugSymbols>
    <DebugType>full</DebugType>
    <Optimize>false</Optimize>
    <OutputPath>bin\Debug\</OutputPath>
    <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
    <ErrorReport>prompt</ErrorReport>
    <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
       <PlatformTarget>AnyCPU</PlatformTarget>
       <DebugType>pdbonly</DebugType>
       <Optimize>true</Optimize>
       <OutputPath>bin\Release\</OutputPath>
       <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
       <ErrorReport>prompt</ErrorReport>
       <WarningLevel>4</WarningLevel>
    </PropertyGroup>

   ```

4. Add this element \<UseDotNetNativeToolchain>true\</UseDotNetNativeToolchain> as a child element to these property groups:

   ```xml

   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">

   ```

5. Delete the following \<ItemGroup> elements:

   ```xml

   <ItemGroup>
      <Compile Include="Properties\AssemblyInfo.cs" />
      <Compile Include="UnitTest.cs" />
   </ItemGroup>
   <ItemGroup>
      <AppxManifest Include="Package.appxmanifest">
         <SubType>Designer</SubType>
      </AppxManifest>
      <None Include="packages.config" />
      <None Include="UnitTestProject1_TemporaryKey.pfx" />
   </ItemGroup>
   <ItemGroup>
      <Content Include="Properties\Default.rd.xml" />
      <Content Include="Assets\Logo.scale-240.png" />
      <Content Include="Assets\SmallLogo.scale-240.png" />
      <Content Include="Assets\SplashScreen.scale-240.png" />
      <Content Include="Assets\Square71x71Logo.scale-240.png" />
      <Content Include="Assets\StoreLogo.scale-240.png" />
      <Content Include="Assets\WideLogo.scale-240.png" />
   </ItemGroup>

   ```

    Reemplácelos por los siguientes elementos:

   ```xml

   <ItemGroup>
      <Compile Include="Properties\AssemblyInfo.cs" />
      <Compile Include="UnitTestApp.xaml.cs">
         <DependentUpon>UnitTestApp.xaml</DependentUpon>
      </Compile>
      <Compile Include="UnitTest.cs" />
   </ItemGroup>
   <ItemGroup>
      <ApplicationDefinition Include="UnitTestApp.xaml">
         <Generator>MSBuild:Compile</Generator>
         <SubType>Designer</SubType>
      </ApplicationDefinition>
   </ItemGroup>
   <ItemGroup>
      <AppxManifest Include="Package.appxmanifest">
         <SubType>Designer</SubType>
      </AppxManifest>
      <None Include="UnitTestProject1_TemporaryKey.pfx" />
   </ItemGroup>
   <ItemGroup>
      <Content Include="Properties\UnitTestApp.rd.xml" />
      <Content Include="Assets\LockScreenLogo.scale-200.png" />
      <Content Include="Assets\SplashScreen.scale-200.png" />
      <Content Include="Assets\Square150x150Logo.scale-200.png" />
      <Content Include="Assets\Square44x44Logo.scale-200.png" />
      <Content Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />
      <Content Include="Assets\StoreLogo.png" />
      <Content Include="Assets\Wide310x150Logo.scale-200.png" />
   </ItemGroup>
   ```

6. Cree un nuevo proyecto de prueba unitaria y copie los archivos UnitTestApp.xaml y UnitTestApp.xaml.cs de dicho proyecto en el proyecto de prueba unitaria existente que está actualizando.

7. Copie el archivo UnitTestApp.rd.xml de la carpeta Propiedades del nuevo proyecto de prueba unitaria en la carpeta Propiedades del proyecto de prueba unitaria existente que está actualizando.

8. Abra el archivo package.appxmanifest en el proyecto. Luego, elimine del archivo los siguientes elementos:

   ```xml

   <Applications>
      <Application Id="vstest.executionengine.universal.App"
            Executable="vstest.executionengine.appcontainer.uap.exe"
            EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">
         <uap:VisualElements
            DisplayName="UnitTestProject1"
            Square150x150Logo="Assets\Logo.png"
            Square44x44Logo="Assets\SmallLogo.png"
            Description="UnitTestProject1"
            BackgroundColor="#464646">
            <uap:SplashScreen Image="Assets\SplashScreen.png" />
         </uap:VisualElements>
      </Application>
   </Applications>
   <Capabilities>
      <Capability Name="internetClientServer" />
   </Capabilities>
   ```

    Reemplace estos elementos eliminados por los siguientes elementos. Use el valor adecuado para ProjectName según el nombre del proyecto, en lugar de UnitTestProject1 en los elementos siguientes:

   ```xml

   <Applications>
      <Application Id="vstest.executionengine.universal.App"
            Executable="$targetnametoken$.exe"
            EntryPoint="UnitTestProject1.App">
         <uap:VisualElements
               DisplayName="UnitTestProject1"
               Square150x150Logo="Assets\Square150x150Logo.png"
               Square44x44Logo="Assets\Square44x44Logo.png"
               Description="UnitTestProject1"
               BackgroundColor="transparent">
            <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>
            <uap:SplashScreen Image="Assets\SplashScreen.png" />
         </uap:VisualElements>
      </Application>
   </Applications>
   <Capabilities>
      <Capability Name="internetClient" />
   </Capabilities>
   ```

   Ahora puede ejecutar las pruebas unitarias.

### <a name="UnitTestRCUpdate10CPlusPlus"></a> Update your C++ projects to use the latest Universal Windows Platform

1. Con Visual Studio, abra la solución que contiene el proyecto de prueba unitaria de C++. Quite los siguientes elementos:

    ```xml

    <TestApplication>true</TestApplication>
    <AppxPackage>True</AppxPackage>
    <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType>
    <EnableCoreRuntime>false</EnableCoreRuntime>

    ```

2. Add the following \<ProjectConfiguration> elements below this element \<ItemGroup Label="ProjectConfigurations"> if they are not already in this fille:

    ```xml

    <ProjectConfiguration Include="Debug|x64">
       <Configuration>Debug</Configuration>
       <Platform>x64</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|x64">
       <Configuration>Release</Configuration>
       <Platform>x64</Platform>
    </ProjectConfiguration>

    ```

3. Reemplace todas las apariciones de este elemento:

    ```xml

    <ConfigurationType>DynamicLibrary</ConfigurationType>

    ```

     Por este:

    ```xml

    <ConfigurationType>Application</ConfigurationType>

    ```

4. Add these \<PropertyGroup> elements if they are not already in the file:

    ```xml

    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'" Label="Configuration">
       <ConfigurationType>Application</ConfigurationType>
       <UseDebugLibraries>true</UseDebugLibraries>
       <PlatformToolset>v140</PlatformToolset>
    </PropertyGroup>
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'" Label="Configuration">
       <ConfigurationType>Application</ConfigurationType>
       <UseDebugLibraries>false</UseDebugLibraries>
       <WholeProgramOptimization>true</WholeProgramOptimization>
       <PlatformToolset>v140</PlatformToolset>
       <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
    </PropertyGroup>

    ```

5. Reemplace todas las apariciones de este elemento:

    ```xml

    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
    ```

     Por este:

    ```xml

    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>

    ```

6. Reemplace todas las apariciones de este elemento:

    ```xml

    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\Lib;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>

    ```

     Por este:

    ```xml

    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>

    ```

7. Add these \<ItemDefinitionGroup> elements in the section that already contains other \<ItemDefinitionGroup> elements:

    ```xml

    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">
       <ClCompile>
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%     (AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
       </ClCompile>
    <Link>
       <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>
    </Link>
    </ItemDefinitionGroup>
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'">
       <ClCompile>
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
       </ClCompile>
       <Link>
          <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>
       </Link>
    </ItemDefinitionGroup>

    ```

8. Delete the following \< ItemGroup> element:

    ```xml

    <ItemGroup>
       <Image Include="Assets\Logo.scale-100.png" />
       <Image Include="Assets\SmallLogo.scale-100.png" />
       <Image Include="Assets\StoreLogo.scale-100.png" />
       <Image Include="Assets\SplashScreen.scale-100.png" />
       <Image Include="Assets\WideLogo.scale-100.png" />
    </ItemGroup>

    ```

     Replace it with this \<ItemGroup> element:

    ```xml

    <ItemGroup>
       <Image Include="Assets\LockScreenLogo.scale-200.png" />
       <Image Include="Assets\SplashScreen.scale-200.png" />
       <Image Include="Assets\Square44x44Logo.scale-200.png" />
       <Image Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />
       <Image Include="Assets\Square150x150Logo.scale-200.png" />
       <Image Include="Assets\StoreLogo.png" />
       <Image Include="Assets\Wide310x150Logo.scale-200.png" />
    </ItemGroup>

    ```

9. Delete the following \< ItemGroup> element:

    ```xml

    <ItemGroup>
       <ClInclude Include="pch.h" />
    </ItemGroup>
    ```

     Replace it with these \<ItemGroup> elements:

    ```xml

    <ItemGroup>
       <ClInclude Include="pch.h" />
       <ClInclude Include="UnitTestApp.xaml.h">
          <DependentUpon>UnitTestApp.xaml</DependentUpon>
       </ClInclude>
    </ItemGroup>
    <ItemGroup>
       <ApplicationDefinition Include="UnitTestApp.xaml">
          <SubType>Designer</SubType>
       </ApplicationDefinition>
    </ItemGroup>

    ```

10. Elimine el siguiente elemento:

    ```xml
    <ClCompile Include="UnitTest.cpp"/>
    ```

     Replace it with these \<CICompile> elements:

    ```xml

    <ClCompile Include="UnitTestApp.xaml.cpp">
       <DependentUpon>UnitTestApp.xaml</DependentUpon>
    </ClCompile>
    <ClCompile Include="UnitTest.cpp"/>

    ```

11. Agregue este elemento:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
    ```

     Agregue este elemento al archivo:

    ```xml

    <ItemGroup>
       <Xml Include="UnitTestApp.rd.xml" />
    </ItemGroup>
    ```

12. Cree un nuevo proyecto de C++ de prueba unitaria y copie los archivos UnitTestApp.xaml, UnitTestApp.xaml.cpp, UnitTestApp.xaml.h y UnitTestApp.rd.xml de ese proyecto en el proyecto existente que va a actualizar.

13. Abra el archivo package.appxmanifest en el proyecto. Luego, elimine del archivo los siguientes elementos:

    ```xml

    <Applications>
       <Application Id="vstest.executionengine.universal.App"
             Executable="vstest.executionengine.appcontainer.uap.exe"
             EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">
          <uap:VisualElements
             DisplayName="UnitTestProject1"
             Square150x150Logo="Assets\Logo.png"
             Square44x44Logo="Assets\SmallLogo.png"
             Description="UnitTestProject1"
             BackgroundColor="#464646">
             <uap:SplashScreen Image="Assets\SplashScreen.png" />
          </uap:VisualElements>
       </Application>
    </Applications>
    <Capabilities>
       <Capability Name="internetClientServer" />
    </Capabilities>

    ```

     Reemplace estos elementos eliminados por los siguientes elementos. Use el valor adecuado para ProjectName según el nombre del proyecto, en lugar de UnitTestProject1 en los elementos siguientes:

    ```xml

    <Applications>
       <Application Id="vstest.executionengine.universal.App"
                Executable="$targetnametoken$.exe"
                EntryPoint="UnitTestProject1.App">
          <uap:VisualElements
                DisplayName="UnitTestProject1"
                Square150x150Logo="Assets\Square150x150Logo.png"
                Square44x44Logo="Assets\Square44x44Logo.png"
                Description="UnitTestProject1"
                BackgroundColor="transparent">
                <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>
                <uap:SplashScreen Image="Assets\SplashScreen.png" />
          </uap:VisualElements>
       </Application>
    </Applications>
    <Capabilities>
       <Capability Name="internetClient" />
    </Capabilities>

    ```