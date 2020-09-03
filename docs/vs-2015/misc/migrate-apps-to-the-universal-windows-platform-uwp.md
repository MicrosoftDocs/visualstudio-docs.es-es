---
title: Migrar aplicaciones al Plataforma universal de Windows (UWP) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5279ab9b-71d9-4be5-81f6-a1f24b06f5fb
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 60951091914474f07f19672799fb59c8b2d0aa56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919135"
---
# <a name="migrate-apps-to-the-universal-windows-platform-uwp"></a>Migrar aplicaciones a la Plataforma universal de Windows (UWP)
Haga los cambios manuales necesarios en los archivos de proyecto existentes para las aplicaciones de la Tienda Windows 8.1, las aplicaciones de Windows Phone 8.1 o las aplicaciones universales de Windows creadas con Visual Studio 2015 RC, de modo que se puedan usar con Visual Studio 2015 RTM. (Si tiene una aplicación universal para Windows 8.1 con un proyecto de aplicación de Windows y un proyecto de Windows Phone, deberá seguir los pasos indicados a continuación para migrar cada proyecto).

 Con la Plataforma universal de Windows ahora puede dirigir su aplicación a una o varias familias de dispositivos. Si desea obtener más información sobre las aplicaciones universales de Windows, vea esta [guía de la plataforma](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx).

- [Migrar las aplicaciones existentes de Windows Phone 8.1 o la Tienda Windows 8.1 C#/VB](#MigrateCSharp) para usar la plataforma universal de Windows.

- [Migrar las aplicaciones existentes de Windows Phone 8.1 o la Tienda Windows 8.1 C++](#MigrateCPlusPlus) para usar la plataforma universal de Windows.

- [Cambios necesarios para las aplicaciones universales de Windows existentes creadas con Visual Studio 2015 RC](#PreviousVersions).

- [Cambios necesarios para los proyectos de prueba unitaria existentes de las aplicaciones universales de Windows creadas con Visual Studio 2015 RC](#MigrateUnitTest).

  Si no desea hacer todos estos cambios, obtenga información sobre cómo [migrar sus aplicaciones existentes](https://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) a un nuevo proyecto universal de Windows.

## <a name="migrate-your-cvb-windows-store-81-or-windows-phone-81-apps-to-use-the-universal-windows-platform"></a><a name="MigrateCSharp"></a> Migrar las aplicaciones de la tienda Windows 8,1 o Windows Phone 8,1 de C#/VB para usar el Plataforma universal de Windows

#### <a name="migrate-your-cvb-project-files"></a>Migrar los archivos de proyecto de C#/VB

1. Para averiguar la plataforma universal de Windows que ha instalado, abra esta carpeta: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Contiene una lista de carpetas para cada plataforma universal de Windows que está instalada. El nombre de la carpeta es la versión de la plataforma universal de Windows que ha instalado. Por ejemplo, este dispositivo Windows 10 tiene la versión 10.0.10240.0 de la Plataforma universal de Windows instalada.

     ![Abra la carpeta para ver las versiones instaladas](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

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

     ![Haga clic con el botón secundario en el proyecto y elija Editar](../misc/media/uap-editproject.png "UAP_EditProject")

6. Busque el \<PropertyGroup> elemento que contiene el \<TargetPlatformVersion> elemento con un valor de 8,1. Siga estos pasos para este \<PropertyGroup> elemento:

    1. Establezca el valor del \<Platform> elemento en: **x86**.

    2. Agregue un \<TargetPlatformIdentifier> elemento y establezca su valor en: **UAP**.

    3. Cambie el valor existente del \<TargetPlatformVersion> elemento para que sea el valor de la versión de plataforma universal de Windows que instaló. Agregue también un \<TargetPlatformMinVersion> elemento y asígnele el mismo valor.

    4. Cambie el valor del \<MinimumVisualStudioVersion> elemento a: **14**.

    5. Reemplace el \<ProjectTypeGuids> elemento como se muestra a continuación:

         Para C#:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
        ```

         Para VB:

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>
        ```

    6. Agregue un \<EnableDotNetNativeCompatibleProfile> elemento y establezca su valor en: **true**.

    7. La escala de activos predeterminada para las aplicaciones universales de Windows es de 200. Si el proyecto incluye activos que no se han escalado en 200, tendrá que agregar un \<UapDefaultAssetScale> elemento con el valor de la escala de los recursos a este propertyGroup. Más información sobre [activos y escalas](https://msdn.microsoft.com/library/jj679352.aspx).

         Ahora el \<PropertyGroup> elemento debe tener un aspecto similar al de este ejemplo:

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

8. Busque \<PropertyGroup> elementos que estén configurados para la plataforma AnyCPU como parte del atributo Condition. Quite estos elementos y todos sus elementos secundarios. AnyCPU no es compatible con las aplicaciones de Windows 10 en Visual Studio 2015. Por ejemplo, debe quitar \<PropertyGroup> elementos como los siguientes:

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

9. Para cada \<PropertyGroup> elemento restante, compruebe si el elemento tiene un atributo Condition con una configuración Release. Si lo hace, pero no contiene un \<UseDotNetNativeToolchain> elemento, agregue uno. Establezca el valor del \<UseDotNetNativeToolchain> elemento en true, de la siguiente manera:

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

10. Solo para los proyectos de Windows Phone, quite el \<PropertyGroup> elemento que contiene un \<TargetPlatformIdentifier> elemento con un valor de WindowsPhoneApp. Asimismo quite los elementos secundarios de este elemento:

    ```xml
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' ">
      <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier>
    </PropertyGroup>
    ```

11. Busque el \<ItemGroup> elemento que contiene el \<AppxManifest> elemento. Agregue el siguiente \<None> elemento como elemento secundario del \<ItemGroup> elemento:

    ```xml
    <None Include="project.json" />
    ```

12. Busque el \<ItemGroup> elemento que contiene otros recursos que se agregan al proyecto, como los archivos logo. png ( \<Content Include="Assets\Logo.scale-100.png" /> ). Agregue el siguiente \<Content> elemento secundario a este \<ItemGroup> elemento:

     **Para C#:**

    ```xml
    <Content Include="Properties\default.rd.xml" />
    ```

     **Para VB:**

    ```xml
    <Content Include="My Project\default.rd.xml" />
    ```

13. Busque el \<ItemGroup> elemento que incluye \<Reference> los elementos secundarios de los paquetes NuGet. Tome nota de los paquetes de NuGet empleados porque deberá descargarlos con el Administrador de paquetes de NuGet cuando se haya vuelto a cargar el proyecto. Quítelo \<ItemGroup> junto con sus elementos secundarios. Por ejemplo, un proyecto UWP podría tener los siguientes paquetes de NuGet que deben quitarse:

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

## <a name="migrate-your-c-windows-store-81-or-windows-phone-81-apps-to-use-the-universal-windows-platform"></a><a name="MigrateCPlusPlus"></a> Migre sus aplicaciones de la tienda Windows de C++ 8,1 o Windows Phone 8,1 para usar el Plataforma universal de Windows

#### <a name="migrate-your-c-project-files"></a>Migrar los archivos de proyecto de C++

1. Para averiguar la plataforma universal de Windows que ha instalado, abra esta carpeta: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Contiene una lista de carpetas para cada plataforma universal de Windows que está instalada. El nombre de la carpeta es la versión de la plataforma universal de Windows que ha instalado. Por ejemplo, este dispositivo Windows 10 tiene la versión 10.0.10240.0 de la Plataforma universal de Windows instalada.

     ![Abra la carpeta para ver las versiones instaladas](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Se puede instalar más de una versión de la plataforma universal de Windows. Se recomienda usar la versión más reciente de la aplicación.

2. Abra la solución que contiene su aplicación existente de Windows Phone 8.1 o la Tienda Windows 8.1 C++ en Visual Studio.

     Haga clic con el botón secundario en el proyecto existente en el Explorador de soluciones y, a continuación, seleccione **Descargar el proyecto**. Después de descargar el proyecto, vuelva a hacer clic con el botón secundario en el archivo de proyecto y elija Editar el archivo .vbproj.

     ![Derecho&#45;haga clic en archivo de proyecto y elija Editar.](../misc/media/uap-editcplusproject.png "UAP_EditCPlusProject")

3. Busque el \<PropertyGroup> elemento que contiene el \<ApplicationTypeRevision> elemento con un valor de 8,1. Siga estos pasos para este \<PropertyGroup> elemento:

    1. Agregue un \<WindowsTargetPlatformVersion> elemento y un \<WindowsTargetPlatformMinVersion> elemento y asígneles el valor de la versión de plataforma universal de Windows que instaló.

    2. Actualice el valor del elemento ApplicationTypeRevision de 8.1 a 10.0.

    3. Cambie el valor del \<MinimumVisualStudioVersion> elemento a: 14.

    4. Agregue un \<EnableDotNetNativeCompatibleProfile> elemento y establezca su valor en: true.

    5. La escala de activos predeterminada para las aplicaciones universales de Windows es de 200. Si el proyecto incluye activos que no se han escalado en 200, tendrá que agregar un \<UapDefaultAssetScale> elemento con el valor de la escala de los recursos a este propertyGroup. Más información sobre [activos y escalas](https://msdn.microsoft.com/library/jj679352.aspx).

    6. Solo para los proyectos de Windows Phone, cambie el valor de \<ApplicationType> de Windows Phone a tienda Windows.

         Ahora el \<PropertyGroup> elemento debe tener un aspecto similar al de este ejemplo:

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

4. Cambie todas las instancias del \<PlatformToolset> elemento para que tengan el valor V140. Por ejemplo:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>
    ```

5. Para cada \<PropertyGroup> elemento restante, compruebe si el elemento tiene un atributo Condition con una configuración Release. Si lo hace, pero no contiene un \<UseDotNetNativeToolchain> elemento, agregue uno. Establezca el valor del \<UseDotNetNativeToolchain> elemento en true, de la siguiente manera:

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

## <a name="update-your-package-manifest-file-for-all-your-windows-store-81-or-windows-phone-81-projects"></a><a name="PackageManifest"></a> Actualice el archivo de manifiesto del paquete para todos los proyectos de la tienda Windows 8,1 o Windows Phone 8,1
 Debe actualizar el archivo de manifiesto del paquete para cada proyecto de la solución.

#### <a name="update-your-package-manifest-file"></a>Actualizar el archivo de manifiesto del paquete

1. Abra el archivo package.appxmanifest en el proyecto. Debe editar el archivo Package.AppxManifest para cada uno de los proyectos de la Tienda Windows y Windows Phone.

2. Debe actualizar el \<Package> elemento con los nuevos esquemas según el tipo de proyecto existente. Primero quite los esquemas siguientes en función de si tiene un proyecto de Windows Phone o la Tienda Windows.

    **Anterior para el proyecto de la tienda Windows:** El \<Package> elemento tendrá un aspecto similar al de este.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
       xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">

   ```

    **Anterior para proyecto de Windows Phone:** El \<Package> elemento tendrá un aspecto similar al de este.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
   xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest"
   xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest"
   xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">
   ```

    **Nuevo para plataforma universal de Windows:** Agregue los esquemas siguientes a su \<Package> elemento. Quite todos los prefijos de identificador de espacio de nombres asociados de los elementos para los esquemas que acaba de quitar. Actualice la propiedad IgnorableNamespaces a: uap mp. El nuevo \<Package> elemento debe tener un aspecto similar a este.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
       xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
       xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
      IgnorableNamespaces= "uap mp">

   ```

3. Agregue un \<Dependencies> elemento secundario al \<Package> elemento. A continuación, agregue un \<TargetDeviceFamily> elemento secundario a este \<Dependencies> elemento con los atributos name, minVersion y MaxVersionTested. Asigne al atributo Name el valor: Windows.Universal. Asigne a los atributos MinVersion y MaxVersionTested el valor de la versión de plataforma universal de Windows que tenga instalada. Este elemento debe ser similar a este.

   ```xml
   <Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" />
   </Dependencies>
   ```

4. **Solo para la tienda Windows:** Debe agregar un \<mp:PhoneIdentity> elemento secundario al \<Package> elemento. Agregue un atributo PhoneProductId y un atributo PhonePublisherId. Establezca PhoneProductId para que tenga el mismo valor que el atributo name en el \<Identity> elemento. Establezca el valor de PhonePublishedId en: 00000000-0000-0000-0000-000000000000. Así:

   ```xml
   <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" />
   <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>
   ```

5. Busque el \<Prerequisites> elemento y elimine este elemento y todos los elementos secundarios que tenga.

6. Agregue el espacio de nombres **UAP** a los siguientes \<Resource> elementos: scale, DXFeatureLevel. Por ejemplo:

   ```xml
   <Resources>
     <Resource Language="en-us"/>
    <Resource uap:Scale="180"/>
    <Resource uap:DXFeatureLevel="dx11"/>
   </Resources>

   ```

7. Agregue el espacio de nombres **UAP** a los siguientes \<Capability> elementos: documentsLibrary, picturesLibrary, videosLibrary, musicLibrary, enterpriseAuthentication, sharedUserCertificates, removableStorage, citas y contactos. Por ejemplo:

   ```xml
   <Capabilities>
     <uap:Capability Name="documentsLibrary"/>
     <uap:Capability Name="removableStorage"/>
   </Capabilities>

   ```

8. Agregue el espacio de nombres **UAP** al \<VisualElements> elemento y a cualquiera de sus elementos secundarios. Por ejemplo:

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

    **Solo se aplica a la Tienda Windows:** los nombres de tamaño de mosaico han cambiado. Cambie los atributos del \<VisualElements> elemento para reflejar los nuevos tamaños de mosaico convergentes. 70 x 70 se convierte en 71 x 71, y 30 x 30 se convierte en 44 x 44.

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

9. Agregue el espacio de nombres **UAP** a \<ApplicationContentUriRules> y a todos sus elementos secundarios. Por ejemplo:

    ```xml
    <uap:ApplicationContentUriRules>
      <uap:Rule Type="include" Match="https://www.microsoft.com/"/>
      <uap:Rule Type="exclude" Match="*.pdf"/>
    </uap:ApplicationContentUriRules>

    ```

10. Agregue el espacio de nombres **UAP** a los siguientes \<Extension> elementos y todos sus elementos secundarios: Windows. accountPictureProvide, Windows. Alarm, Windows. AppointmentsProvider Windows. autoPlayContent, Windows. autoPlayDevice, Windows. cachedFileUpdate, Windows. cameraSettings, Windows. fileOpenPicker, Windows. fileTypeAssociation, Windows. fileSavePicke, Windows. lockScreenCall, Windows. printTaskSettings, Windows. Protocol, Windows. Search, Windows. shareTarget. Por ejemplo:

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

12. Cambie las dependencias del marco. Agregue un nombre de publicador a todos los \<PackageDependency> elementos y especifique un MinVersion si aún no se ha especificado.

     **Antigua:** \<PackageDependency> Element

    ```xml
    <Dependencies>
     <PackageDependency Name="Microsoft.VCLibs.120.00" />
    </Dependencies>

    ```

     **Nuevo:** \<PackageDependency> Element

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

     **ANTIGÜEDAD**

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

     **ANTIGÜEDAD**

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

    1. Estos atributos de \<VisualElements> están desusados y deben quitarse:

       - Los \<VisualElements> atributos: ForegroundText, ToastCapable

       - El \<DefaultTile> atributo DefaultSize

       - El elemento \<ApplicationView>

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

    1. Abra el Explorador de archivos, haga clic en **Vista** en la barra de herramientas y seleccione **Elementos ocultos** y **Extensiones de nombre de archivo**. Abra esta carpeta en el equipo: \<path for the location of your solution> \\ . vs \\ {nombre del proyecto} \v14. Si hay un archivo con una extensión de archivo .suo, elimínelo.

    2. Ahora vuelva a la carpeta donde se encuentra la solución. Abra las carpetas de los proyectos que existen en la solución. Si un archivo dentro de cualquiera de estas carpetas de proyecto tiene una extensión .csproj.user o .vbproj.user, elimínelo.

         Ahora puede volver a abrir la solución en Visual Studio. Está listo para codificar, compilar y depurar la aplicación con la plataforma universal de Windows.

         Aprenda a [adaptar el código](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) para sacar el máximo partido a las novedades de la Plataforma universal de Windows.

## <a name="changes-required-for-existing-universal-windows-apps-created-with-visual-studio-2015-rc"></a><a name="PreviousVersions"></a> Cambios necesarios para las aplicaciones universales de Windows existentes creadas con Visual Studio 2015 RC
 Si creó aplicaciones universales de Windows 10 con Visual Studio 2015 RC, debe redirigir el proyecto para usar la versión de la Plataforma universal de Windows instalada con la versión más reciente de Visual Studio 2015. Las versiones anteriores no son compatibles. Los cambios necesarios son diferentes según el idioma utilizado para crear la aplicación:

- [Aplicaciones C#/VB](#RCUpdate10CSharp)

- [Aplicaciones de C++](#RCUpdate10CPlusPlus)

### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a><a name="RCUpdate10CSharp"></a> Actualización de los proyectos de C#/VB para usar la Plataforma universal de Windows más reciente
 Al abrir la solución de la aplicación existente, verá que la aplicación necesita una actualización:

 ![Ver el proyecto en el Explorador de soluciones](../misc/media/uwp-updaterequired.png "UWP_UpdateRequired")

 Si decide volver a cargar este proyecto desde el Explorador de soluciones, verá este cuadro de diálogo:

 ![Redirigir la aplicación para que use el SDK correcto](../misc/media/missingsdkforuap.png "MissingSDKforUAP")

 Dado que el SDK de la plataforma universal de Windows para el proyecto no es compatible por el momento, no podrá instalarlo. Simplemente haga clic en Aceptar y siga estos pasos.

##### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a>Actualizar los proyectos C#/VB para que usen la plataforma universal de Windows más reciente

1. Para averiguar la plataforma universal de Windows que ha instalado, abra esta carpeta: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Contiene una lista de carpetas para cada plataforma universal de Windows que está instalada. El nombre de la carpeta es la versión de la plataforma universal de Windows que ha instalado. Por ejemplo, este dispositivo Windows 10 tiene la versión 10.0.10240.0 de la Plataforma universal de Windows instalada.

    ![Abra la carpeta para ver las versiones instaladas](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

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

    ![Haga clic con el botón secundario en el proyecto y elija Editar](../misc/media/uap-editproject.png "UAP_EditProject")

4. Busque el \<PropertyGroup> elemento que contiene los \<TargetPlatformVersion> \<TargetPlatformMinVersion> elementos y. Cambie el valor existente de los \<TargetPlatformVersion> \<TargetPlatformMinVersion> elementos y para que sea la misma versión del plataforma universal de Windows que ha instalado.

    La escala de activos predeterminada para las aplicaciones universales de Windows es de 200. Los proyectos creados con Visual Studio 2015 RC incluían los recursos escalados en 100, deberá agregar un \<UapDefaultAssetScale> elemento con un valor de 100 a este propertyGroup. Más información sobre [activos y escalas](https://msdn.microsoft.com/library/jj679352.aspx).

5. Si agregó referencias a los SDK de extensión de UWP (por ejemplo, el SDK de Windows Mobile), deberá actualizar la versión del SDK. Por ejemplo, este \<SDKReference> elemento:

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

6. Busque el \<Target> elemento con un atributo de nombre que tenga el valor: EnsureNuGetPackageBuildImports. Elimine este elemento y todos sus elementos secundarios.

   ```xml
   <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">
       <PropertyGroup>
         <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>
       </PropertyGroup>
       <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" />
       <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" />
   </Target>
   ```

7. Busque y elimine los \<Import> elementos con los atributos Project y Condition que hacen referencia a Microsoft. Diagnostics. Tracing. EventSource y a Microsoft. ApplicationInsights, de la siguiente manera:

   ```xml
   <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" />
   <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />

   ```

8. Busque el \<ItemGroup> elemento que tiene \<Reference> elementos secundarios en paquetes NuGet. Tome nota de los paquetes de NuGet referenciados, ya que necesitará esta información para un paso posterior. Una diferencia significativa del formato de proyecto de Windows 10 entre Visual Studio 2015 RC y Visual Studio 2015 RTM es que el formato RTM usa [NuGet](/nuget/) versión 3.

    Quite el \<ItemGroup> y todos sus elementos secundarios. Por ejemplo, un proyecto UWP creado con Visual Studio RC tendrá los siguientes paquetes de NuGet que se deben quitar:

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

9. Busque el \<ItemGroup> elemento que contiene un \<AppxManifest> elemento. Si hay un \<None> elemento con un atributo Include establecido en: packages.config, elimínelo. Además, agregue un \<None> elemento con un atributo Include y establezca su valor en: project.jsen.

10. Guarde los cambios. Después cierre el archivo de proyecto.

11. Haga clic con el botón secundario en el archivo de proyecto en el Explorador de soluciones y elija Volver a cargar el proyecto en el menú contextual. Todos los archivos del proyecto ahora deben aparecer en el Explorador de soluciones.

12. Seleccione el archivo ApplicationInsights.config en el Explorador de soluciones y abra sus propiedades. Establezca la propiedad Acción de compilación en "Contenido" y la propiedad Copiar en el directorio de salida en "Copiar si es posterior".

13. Abra el archivo package.appxmanifest en el proyecto.

    1. Busque el elemento \<TargetDeviceFamily> . Cambie los atributos MinVersion y MaxVersionTested para que correspondan con la versión de Plataforma universal de Windows que tenga instalada. Así:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Guarde los cambios.

14. Use el Administrador de NuGet para agregar los paquetes que eliminó en el paso anterior. Una diferencia significativa del formato de proyecto de Windows 10 entre Visual Studio 2015 RC y Visual Studio 2015 RTM es que el formato RTM usa [NuGet](/nuget/) versión 3.

    Ahora puede codificar, compilar y depurar la aplicación.

    Si tiene proyectos de prueba unitaria para sus aplicaciones universales de Windows, también debe seguir [estos pasos](#MigrateUnitTest).

### <a name="update-your-c-projects-to-use-the-latest-universal-windows-platform"></a><a name="RCUpdate10CPlusPlus"></a> Actualice los proyectos de C++ para usar la Plataforma universal de Windows más reciente

1. Para averiguar la plataforma universal de Windows que ha instalado, abra esta carpeta: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Contiene una lista de carpetas para cada plataforma universal de Windows que está instalada. El nombre de la carpeta es la versión de la plataforma universal de Windows que ha instalado. Por ejemplo, este dispositivo Windows 10 tiene la versión 10.0.10240.0 de la Plataforma universal de Windows instalada.

     ![Abra la carpeta para ver las versiones instaladas](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Se puede instalar más de una versión de la plataforma universal de Windows. Se recomienda usar la versión más reciente de la aplicación.

2. Abra la solución que contiene la aplicación universal de Windows de C++. Haga clic con el botón secundario en el archivo .vcxproj del proyecto y elija descargar el archivo de proyecto. Después de descargar el proyecto, vuelva a hacer clic con el botón secundario en el archivo de proyecto y elija editarlo.

     ![Descargue el proyecto y, a continuación, edite el archivo del proyecto](../misc/media/uap-editearliercplus.png "UAP_EditEarlierCPlus")

3. Busque \<PropertyGroup> elementos que no contengan un atributo Condition pero que contengan un \<ApplicationTypeRevision> elemento. Actualice el valor ApplicationTypeRevision de 8.2 a 10.0. Agregue un \<WindowsTargetPlatformVersion> elemento y un \<WindowsTargetPlatformMinVersion> elemento y establezca sus valores para que sea el valor de la versión de plataforma universal de Windows que instaló.

     Agregue un \<EnableDotNetNativeCompatibleProfile> elemento y establezca su valor en true si el elemento no existe todavía.

     La escala de activos predeterminada para las aplicaciones universales de Windows es de 200. Los proyectos creados con Visual Studio 2015 RC incluían los recursos escalados en 100, deberá agregar un \<UapDefaultAssetScale> elemento con un valor de 100 a este propertyGroup. Más información sobre [activos y escalas](https://msdn.microsoft.com/library/jj679352.aspx).

     Por lo tanto, este \<PropertyGroup> elemento será similar al siguiente:

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

4. Para cada \<PropertyGroup> elemento restante, compruebe si el elemento tiene un atributo Condition con una configuración Release. Si lo hace, pero no contiene un \<UseDotNetNativeToolchain> elemento, agregue uno. Establezca el valor del \<UseDotNetNativeToolchain> elemento en true, de la siguiente manera:

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

5. Debe actualizar el \<EnableDotNetNativeCompatibleProfile> elemento y el \<UseDotNetNativeToolchain> elemento para habilitar .net Native, pero .net Native no está habilitado en las plantillas de C++.

     Guarde los cambios. Después cierre el archivo de proyecto.

6. Haga clic con el botón secundario en el archivo de proyecto en el Explorador de soluciones y elija Volver a cargar el proyecto en el menú contextual. Todos los archivos del proyecto ahora deben aparecer en el Explorador de soluciones.

7. Abra el archivo package.appxmanifest en el proyecto.

    1. Busque el elemento \<TargetDeviceFamily> . Cambie los atributos MinVersion y MaxVersionTested para que correspondan con la versión de Plataforma universal de Windows que tenga instalada. Así:

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Guarde los cambios.

         Ahora puede codificar, compilar y depurar la aplicación.

         Si tiene proyectos de prueba unitaria para sus aplicaciones universales de Windows, también debe seguir [estos pasos](#MigrateUnitTest).

## <a name="changes-required-for-existing-unit-test-projects-for-universal-windows-apps-created-with-visual-studio-2015-rc"></a><a name="MigrateUnitTest"></a> Cambios necesarios para los proyectos de prueba unitaria existentes para las aplicaciones universales de Windows creadas con Visual Studio 2015 RC
 Si creó proyectos de prueba unitaria para aplicaciones universales de Windows 10 con Visual Studio 2015 RC, debe hacer estos cambios adicionales en los archivos de proyecto para usar dichos proyectos de prueba con la versión más reciente de Visual Studio 2015. Los cambios necesarios son diferentes según el idioma utilizado para crear la aplicación:

- [Aplicaciones C#/VB](#UnitTestRCUpdate10CSharp)

- [Aplicaciones de C++](#UnitTestRCUpdate10CPlusPlus)

### <a name="update-your-cvb-unit-test-projects"></a><a name="UnitTestRCUpdate10CSharp"></a> Actualización de los proyectos de prueba unitaria de C#/VB

1. Con Visual Studio, abra la solución que contiene el proyecto de prueba unitaria de C#/VB. Cambie el valor del \<OuttputType> elemento a: AppContainerExe.

   ```xml

   <OutputType>AppContainerExe</OutputType>

   ```

2. Reemplace este elemento \<EnableCoreRuntime> false \</EnableCoreRuntime> por el elemento siguiente:

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

4. Agregue este elemento \<UseDotNetNativeToolchain> true \</UseDotNetNativeToolchain> como elemento secundario a estos grupos de propiedades:

   ```xml

   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">

   ```

5. Elimine los siguientes \<ItemGroup> elementos:

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

### <a name="update-your-c-projects-to-use-the-latest-universal-windows-platform"></a><a name="UnitTestRCUpdate10CPlusPlus"></a> Actualice los proyectos de C++ para usar la Plataforma universal de Windows más reciente

1. Con Visual Studio, abra la solución que contiene el proyecto de prueba unitaria de C++. Quite los siguientes elementos:

    ```xml

    <TestApplication>true</TestApplication>
    <AppxPackage>True</AppxPackage>
    <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType>
    <EnableCoreRuntime>false</EnableCoreRuntime>

    ```

2. Agregue los siguientes \<ProjectConfiguration> elementos debajo de este elemento \<ItemGroup Label="ProjectConfigurations"> si aún no están en este relleno:

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

4. Agregue estos \<PropertyGroup> elementos si aún no están en el archivo:

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

7. Agregue estos \<ItemDefinitionGroup> elementos a la sección que ya contiene otros \<ItemDefinitionGroup> elementos:

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

8. Elimine el siguiente \< ItemGroup> elemento:

    ```xml

    <ItemGroup>
       <Image Include="Assets\Logo.scale-100.png" />
       <Image Include="Assets\SmallLogo.scale-100.png" />
       <Image Include="Assets\StoreLogo.scale-100.png" />
       <Image Include="Assets\SplashScreen.scale-100.png" />
       <Image Include="Assets\WideLogo.scale-100.png" />
    </ItemGroup>

    ```

     Reemplácelo por este \<ItemGroup> elemento:

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

9. Elimine el siguiente \< ItemGroup> elemento:

    ```xml

    <ItemGroup>
       <ClInclude Include="pch.h" />
    </ItemGroup>
    ```

     Reemplácelo por estos \<ItemGroup> elementos:

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

     Reemplácelo por estos \<CICompile> elementos:

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