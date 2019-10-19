---
title: 'Tutorial: Crear un entorno de compilación para varios equipos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building on multiple computers
- build environment, MSBuild
ms.assetid: ae5391b1-3eec-42f5-beb3-f28630615a9e
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d0fccb5694e538cdf71844d2cc18640114ec735
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672308"
---
# <a name="walkthrough-creating-a-multiple-computer-build-environment"></a>Tutorial: Crear un entorno de compilación para varios equipos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se puede crear un entorno de compilación dentro de la organización si se instala Visual Studio en un equipo host y después se copian los diversos archivos y configuraciones en otro equipo para que pueda participar en las compilaciones. No es necesario instalar Visual Studio en el otro equipo.

 Este documento no confiere ningún derecho para redistribuir el software externamente ni para proporcionar entornos de compilación a terceros.

||
|-|
|Declinación de responsabilidades<br /><br /> Este documento se proporciona "tal cual". Si bien hemos probado los pasos descritos, no es posible probar de forma exhaustiva todas las configuraciones. Intentaremos mantener el documento actualizado con cualquier información adicional que aprendamos. La información y los puntos de vista expresados en este documento, incluidas las direcciones URL y otras referencias a sitios web de Internet, pueden cambiar sin previo aviso. Microsoft no proporciona ninguna garantía, expresa o implícita, con respecto a la información proporcionada aquí. Usted asume el riesgo de utilizarla.<br /><br /> Este documento no le proporciona ningún derecho legal sobre ninguna propiedad intelectual de ningún producto de Microsoft. Puede copiar y usar este documento para su uso interno de referencia.<br /><br /> No tiene ninguna obligación de proporcionar a Microsoft ninguna sugerencia ni ningún comentario ("Comentario”) con respecto a este documento. Sin embargo, cualquier Comentario que proporcione voluntariamente se puede utilizar en productos de Microsoft y especificaciones relacionadas u otra documentación (denominados colectivamente "Ofertas de Microsoft") que a su vez pueden utilizar terceros para desarrollar sus propios productos. Por tanto, si proporciona Comentarios a Microsoft sobre cualquier versión de este documento o las Ofertas de Microsoft a las que se aplican, acepta lo siguiente: (a) Microsoft puede utilizar, reproducir, licenciar, distribuir y comercializar libremente sus Comentarios sobre cualquier Oferta de Microsoft; (b) También concede a terceros, de forma gratuita, únicamente los derechos de patente necesarios para permitir que otros productos utilicen o interactúen con cualquier parte determinada de un Producto de Microsoft que incorpore sus Comentarios; y (c) No ofrecerá a Microsoft Comentarios (i) que tenga razones para creer que están sujetos a cualquier patente, copyright u otro derecho o reclamación de propiedad intelectual de cualquier tercero; o (ii) sujetos a términos de licencia que obliguen a que cualquier Oferta de Microsoft que incorpore o derive de esos Comentarios, u otra propiedad intelectual de Microsoft, se ofrezca en licencia o se comparta de otra forma con ningún tercero.|

 Este tutorial se ha validado en los siguientes sistemas operativos, ejecutando MSBuild en la línea de comandos y mediante Team Foundation Build.

- Windows 8 (x86 y x64)

- Windows 7 Ultimate

- Windows Server 2008 R2 Standard

  Después de completar los pasos de este tutorial, puede utilizar el entorno de varios equipos para compilar estas clases de aplicaciones:

- Aplicaciones de escritorio de C++ que utilizan Windows 8 SDK

- Aplicaciones de escritorio de Visual Basic o C# destinadas a .NET Framework 4.5

  El entorno de varios equipos no se puede utilizar para compilar estas clases de aplicaciones:

- Aplicaciones de la [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)]. Para compilar aplicaciones de la [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], debe instalar Visual Studio en el equipo de compilación.

- Aplicaciones de escritorio destinadas a .NET Framework 4 o anterior. Para compilar estas clases de aplicaciones, debe instalar Visual Studio o ensamblados de referencia y herramientas de .NET (de Windows 7.1 SDK) en el equipo de compilación.

  Este tutorial está dividido en estas partes:

- [Instalar software en los equipos](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingSoftware)

- [Copiar archivos del equipo host al equipo de compilación](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles)

- [Crear la configuración del Registro](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingRegistry)

- [Establecer variables de entorno en el equipo de compilación](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#SettingEnvVariables)

- [Instalar ensamblados de MSBuild en la caché global de ensamblados (GAC) en el equipo de compilación](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC)

- [Compilar proyectos](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#BuildingProjects)

- [Crear el entorno de compilación para que se pueda proteger en el control de código fuente](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingForSourceControl)

## <a name="prerequisites"></a>Requisitos previos

- Una copia con licencia de Visual Studio Ultimate, Visual Studio Premium o Visual Studio Professional

- Una copia de .NET Framework 4.5.1, que se puede descargar del sitio web de [Microsoft](https://www.microsoft.com/download/details.aspx?id=40779).

## <a name="InstallingSoftware"></a> Instalar software en los equipos
 En primer lugar, configure el equipo host y configure después el equipo de compilación.

 Al instalar Visual Studio en el equipo host, se crean los archivos y las configuraciones que copiará al equipo de compilación más adelante. Puede instalar Visual Studio en un equipo x86 o x64, pero la arquitectura del equipo de compilación debe coincidir con la arquitectura del equipo host.

#### <a name="to-install-software-on-the-computers"></a>Para instalar software en los equipos

1. En el equipo host, instale Visual Studio.

2. En el equipo de compilación, instale .NET Framework 4.5. Para comprobar que está instalado, asegúrese de que el valor de la clave del Registro HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full@Version comienza con "4.5".

## <a name="CopyingFiles"></a> Copiar archivos del equipo host al equipo de compilación
 En esta sección se explica cómo copiar los archivos, compiladores, herramientas de compilación, activos de MSBuild y configuraciones del Registro necesarios del equipo host al equipo de compilación. En estas instrucciones se da por supuesto que ha instalado Visual Studio en la ubicación predeterminada en el equipo host; si lo instaló en otra ubicación, ajuste los pasos en consecuencia.

- En un equipo x86, la ubicación predeterminada es C:\Archivos de programa\Microsoft Visual Studio 11.0\

- En un equipo x64, la ubicación predeterminada es C:\Archivos de programa (x86)\Microsoft Visual Studio 11.0\

  Tenga en cuenta que el nombre de la carpeta Archivos de programa depende del sistema operativo instalado. En un equipo x86, el nombre es \Archivos de programa\\, mientras que en un equipo x64 es \Archivos de programa (x86)\\. Con independencia de la arquitectura del sistema, este tutorial hace referencia a la carpeta Archivos de programa como %ProgramFiles%.

> [!NOTE]
> En el equipo de compilación, todos los archivos pertinentes deben estar en la misma unidad; sin embargo, la letra de esa unidad puede ser diferente que la de la unidad donde está instalado Visual Studio en el equipo host. En cualquier caso, debe tener en cuenta la ubicación de los archivos cuando cree entradas del Registro como se describe más adelante en este documento.

#### <a name="to-copy-the-windows-sdk-files-to-the-build-computer"></a>Para copiar los archivos de Windows SDK en el equipo de compilación

1. Si solo tiene instalado Windows SDK para Windows 8, copie estas carpetas de forma recursiva del equipo host al equipo de compilación:

   - %ProgramFiles%\Windows Kits\8.0\bin\

   - %ProgramFiles%\Windows Kits\8.0\Catalogs\

   - %ProgramFiles%\Windows Kits\8.0\DesignTime\

   - %ProgramFiles%\Windows Kits\8.0\include\

   - %ProgramFiles%\Windows Kits\8.0\Lib\

   - %ProgramFiles%\Windows Kits\8.0\Redist\

   - %ProgramFiles%\Windows Kits\8.0\References\

     Si tiene también estos otros kits de Windows 8…

   - Microsoft Windows Assessment and Deployment Kit

   - Kit para controladores de Microsoft Windows

   - Kit para la certificación de hardware en Microsoft Windows

     …pueden tener instalados archivos en las carpetas %ProgramFiles%\Windows Kits\8.0\ enumeradas en el paso anterior, y sus términos de licencia quizás no permitan derechos de servidor de compilación para esos archivos. Consulte los términos de licencia de todos los kits de Windows instalados para comprobar si se pueden copiar archivos en el equipo de compilación. Si los términos de licencia no permiten derechos de servidor de compilación, quite los archivos del equipo de compilación.

2. Copie las siguientes carpetas de forma recursiva del equipo host al equipo de compilación:

   - %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\

   - %ProgramFiles%\Common Files\Merge Modules\

   - %ProgramFiles%\Microsoft Visual Studio 11.0\VC\

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\ProjectComponents\

   - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\V110\

   - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5\

   - %ProgramFiles%\Reference Assemblies\Microsoft\Framework\\.NETFramework\v4.5\

3. Copie estos archivos del equipo host al equipo de compilación:

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\msobj110.dll

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdb110.dll

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdbcore.dll

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\mspdbsrv.exe

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\msvcdis110.dll

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\makehm.exe

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\VCVarsQueryRegistry.bat

   - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\Tools\vsvars32.bat

4. Las siguientes bibliotecas en tiempo de ejecución de Visual C++ solo se requieren si ejecuta resultados de la compilación en el equipo de compilación, por ejemplo, como parte de pruebas automatizadas. Los archivos suelen encontrarse en subcarpetas bajo la carpeta %ProgramFiles%\Microsoft Visual Studio 11.0\VC\redist\x86\ o %ProgramFiles%\Microsoft Visual Studio 11.0\VC\redist\x64\, según la arquitectura del sistema. En los sistemas x86, copie los archivos binarios x86 a la carpeta \Windows\System32\. En los sistemas x64, copie los archivos binarios x86 a la carpeta Windows\SysWOW64\ y los archivos binarios x64 a la carpeta Windows\System32\.

   - \Microsoft.VC110.ATL\atl110.dll

   - \Microsoft.VC110.CRT\msvcp110.dll

   - \Microsoft.VC110.CRT\msvcr110.dll

   - \Microsoft.VC110.CXXAMP\vcamp110.dll

   - \Microsoft.VC110.MFC\mfc110.dll

   - \Microsoft.VC110.MFC\mfc110u.dll

   - \Microsoft.VC110.MFC\mfcm110.dll

   - \Microsoft.VC110.MFC\mfcm110u.dll

   - \Microsoft.VC110.MFCLOC\mfc110chs.dll

   - \Microsoft.VC110.MFCLOC\mfc110cht.dll

   - \Microsoft.VC110.MFCLOC\mfc110deu.dll

   - \Microsoft.VC110.MFCLOC\mfc110enu.dll

   - \Microsoft.VC110.MFCLOC\mfc110esn.dll

   - \Microsoft.VC110.MFCLOC\mfc110fra.dll

   - \Microsoft.VC110.MFCLOC\mfc110ita.dll

   - \Microsoft.VC110.MFCLOC\mfc110jpn.dll

   - \Microsoft.VC110.MFCLOC\mfc110kor.dll

   - \Microsoft.VC110.MFCLOC\mfc110rus.dll

   - \Microsoft.VC110.OPENMP\vcomp110.dll

5. Copie solo los siguientes archivos de la carpeta \Debug_NonRedist\x86\ o \Debug_NonRedist\x64\ al equipo de compilación, como se describe en [Preparar un equipo de pruebas para ejecutar un archivo ejecutable de depuración](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable). No se puede copiar ningún otro archivo.

   - \Microsoft.VC110.DebugCRT\msvcp110d.dll

   - \Microsoft.VC110.DebugCRT\msvcr110d.dll

   - \Microsoft.VC110.DebugCXXAMP\vcamp110d.dll

   - \Microsoft.VC110.DebugMFC\mfc110d.dll

   - \Microsoft.VC110.DebugMFC\mfc110ud.dll

   - \Microsoft.VC110.DebugMFC\mfcm110d.dll

   - \Microsoft.VC110.DebugMFC\mfcm110ud.dll

   - \Microsoft.VC110.DebugOpenMP\vcomp110d.dll

## <a name="CreatingRegistry"></a> Crear la configuración del Registro
 Debe crear entradas del Registro para configurar los valores de MSBuild.

#### <a name="to-create-registry-settings"></a>Para crear la configuración del Registro

1. Identifique la carpeta primaria para las entradas del Registro. Todas las entradas del Registro se crean bajo la misma clave primaria. En un equipo x86, la clave primaria es HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. En un equipo x64, la clave primaria es HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Con independencia de la arquitectura del sistema, en este tutorial se hace referencia a la clave primaria como %RegistryRoot%.

   > [!NOTE]
   > Si la arquitectura del equipo host es distinta de la del equipo de compilación, asegúrese de utilizar la clave primaria adecuada en cada equipo. Esto es especialmente importante si desea automatizar el proceso de exportación.
   >
   >  Además, si en el equipo de compilación usa otra letra de unidad que en el equipo host, asegúrese de cambiar los valores de las entradas del Registro para que coincidan.

2. Cree las entradas del Registro siguientes en el equipo de compilación. Todas estas entradas son cadenas (Tipo == "REG_SZ" en el Registro). Establezca los mismos valores para estas entradas y para las entradas comparables en el equipo host.

   - %RegistryRoot%\\.NETFramework\v4.0.30319\AssemblyFoldersEx\VCMSBuild Public Assemblies@(Default)

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0@InstallationFolder

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A@InstallationFolder

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools@InstallationFolder

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x86@InstallationFolder

   - %RegistryRoot%\VisualStudio\11.0@Source Directories

   - %RegistryRoot%\VisualStudio\11.0\Setup\VC@ProductDir

   - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir32

   - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkDir64

   - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer32

   - %RegistryRoot%\VisualStudio\SxS\VC7@FrameworkVer64

   - %RegistryRoot%\VisualStudio\SxS\VC7@11.0

   - %RegistryRoot%\VisualStudio\SxS\VS7@11.0

   - %RegistryRoot%\Windows Kits\Installed Roots@KitsRoot

   - %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath

   - %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10

   - %RegistryRoot%\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11

     En un equipo de compilación x64, cree también siguiente la entrada del Registro y consulte el equipo host para determinar cómo establecerla.

   - %RegistryRoot%\Microsoft SDKs\Windows\v8.0A\WinSDK-NetFx40Tools-x64@InstallationFolder

     Si el equipo de compilación es x64 y desea utilizar la versión de 64 bits de MSBuild, o si está utilizando el servicio de compilación de Team Foundation Server en un equipo x64, debe crear las entradas del Registro siguientes en el registro nativo de 64 bits. Consulte el equipo host para determinar cómo establecer estas entradas.

   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Setup\VS@ProductDir

   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath

   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath10

   - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\4.0\11.0@VCTargetsPath11

## <a name="SettingEnvVariables"></a> Establecer variables de entorno en el equipo de compilación
 Para utilizar MSBuild en el equipo de compilación, debe establecer las variables de entorno PATH. Puede utilizar vcvarsall.bat para establecer las variables o puede configurarlas manualmente.

#### <a name="to-use-vcvarsallbat-to-set-environment-variables"></a>Para utilizar vcvarsall.bat con el fin de establecer variables de entorno

- Abra una ventana de símbolo del sistema en el equipo de compilación y ejecute %Program Files%\Microsoft Visual Studio 11.0\VC\vcvarsall.bat. Puede usar un argumento de línea de comandos para especificar el conjunto de herramientas que desea usar: x86, x64 nativo o compilador cruzado de x64. Si no especifica ningún argumento de la línea de comandos, se utiliza el conjunto de herramientas de x86.

     En esta tabla se describen los argumentos admitidos para vcvarsall.bat:

    |Argumento de vcvarsall.bat|Compilador|Arquitectura del equipo de compilación|Arquitectura de salida de compilación|
    |----------------------------|--------------|---------------------------------|-------------------------------|
    |x86 (predeterminado)|Nativo de 32 bits|x86, x64|x86|
    |x86_amd64|Cruzado de x64|x86, x64|x64|
    |amd64|Nativo de x64|x64|x64|

     Si vcvarsall.bat se ejecuta correctamente (es decir, no se muestra ningún mensaje de error), puede omitir el paso siguiente y continuar a la sección [Instalar ensamblados de MSBuild en la caché global de ensamblados (GAC) en el equipo de compilación](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC) de este documento.

#### <a name="to-manually-set-environment-variables"></a>Para establecer manualmente variables de entorno

1. Para configurar manualmente el entorno de la línea de comandos, agregue esta ruta de acceso a la variable de entorno PATH:

   - %Program Files%\Microsoft Visual Studio 11.0\Common7\IDE

2. Opcionalmente, también puede agregar las rutas de acceso siguientes a la variable PATH para que sea más fácil usar MSBuild para compilar las soluciones.

    Si desea utilizar MSBuild nativo de 32 bits, agregue estas rutas de acceso a la variable PATH:

   - %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools

   - %windir%\Microsoft.NET\Framework\v4.0.30319

     Si quiere usar MSBuild nativo de 64 bits, agregue estas rutas de acceso a la variable PATH:

   - %Program Files%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\x64

   - %windir%\Microsoft.NET\Framework64\v4.0.30319

## <a name="InstallingMSBuildToGAC"></a> Instalar ensamblados de MSBuild en la caché global de ensamblados (GAC) en el equipo de compilación
 MSBuild requiere la instalación de algunos ensamblados adicionales en la GAC del equipo de compilación.

#### <a name="to-copy-assemblies-from-the-host-computer-and-install-them-on-the-build-computer"></a>Para copiar los ensamblados del equipo host e instalarlos en el equipo de compilación

1. Copie los ensamblados siguientes del equipo host al equipo de compilación. Como se instalarán en la GAC, puede ponerlos en cualquier lugar del equipo de compilación.

    - %ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.Build.CPPTasks.Common.v110.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\CommonExtensions\Microsoft\VC\Project\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll

    - %ProgramFiles%\Microsoft Visual Studio 11.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.VCProjectEngine.dll

2. Para instalar los ensamblados en la GAC, busque gacutil.exe en el equipo de compilación; normalmente está en %ProgramFiles%\Microsoft SDKs\Windows\v8.0A\bin\NETFX 4.0 Tools\\. Si no encuentra esta carpeta, repita los pasos de la sección [Copiar archivos del equipo host al equipo de compilación](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) de este tutorial.

     Abra una ventana de símbolo del sistema que tenga derechos administrativos y ejecute este comando para cada archivo:

     **gacutil -i \<file>**

    > [!NOTE]
    > Puede que sea necesario reiniciar el sistema para que un ensamblado se instale totalmente en la GAC.

## <a name="BuildingProjects"></a> Compilar proyectos
 Puede utilizar Team Foundation Build para compilar proyectos y soluciones de [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] o puede compilarlos en la línea de comandos. Cuando se utiliza Team Foundation Build para compilar proyectos, invoca el ejecutable de MSBuild correspondiente a la arquitectura del sistema.  En la línea de comandos, puede utilizar MSBuild de 32 bits o MSBuild 64 bits, y puede elegir la arquitectura de MSBuild estableciendo la variable de entorno PATH o invocando directamente el archivo ejecutable de MSBuild específico de la arquitectura.

 Para usar msbuild.exe en el símbolo del sistema, ejecute el comando siguiente, donde *solution.sln* es un marcador de posición para el nombre de la solución.

 **msbuild** *solution.sln*

 Para más información sobre cómo usar MSBuild en la línea de comandos, vea [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).

> [!NOTE]
> Para compilar proyectos de [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], debe utilizar el Conjunto de herramientas de la plataforma "v110". Si no desea editar los archivos de proyecto de [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], puede establecer el Conjunto de herramientas de la plataforma mediante este argumento de la línea de comandos:
>
> **msbuild** *solution.sln* **/p:PlatformToolset=v110**

## <a name="CreatingForSourceControl"></a> Crear el entorno de compilación para que se pueda proteger en el control de código fuente
 Puede crear un entorno de compilación que se pueda implementar en varios equipos y no requiera almacenar archivos en la GAC ni modificar configuraciones del Registro. Los pasos siguientes son simplemente una forma de realizarlo. Adapte estos pasos a las características únicas de su entorno de compilación.

> [!NOTE]
> Debe deshabilitar la compilación incremental de modo que tracker.exe no produzca ningún error durante una compilación. Para deshabilitar la compilación incremental, establezca este parámetro de compilación:
>
> **msbuild** *solution.sln* **/p:TrackFileAccess=false**

#### <a name="to-create-a-build-environment-that-can-be-checked-into-source-control"></a>Para crear un entorno de compilación que se pueda proteger en el control de código fuente

1. Cree un directorio "Depot" en el equipo host.

     En estos pasos se hace referencia al directorio como %Depot%.

2. Copie los directorios y los archivos como se describe en la sección [Copiar archivos del equipo host al equipo de compilación](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) de este tutorial, pero péguelos en el directorio %Depot% recién creado. Por ejemplo, copie de %ProgramFiles%\Windows Kits\8.0\bin\ a %Depot%\Windows Kits\8.0\bin\\.

3. Cuando los archivos se hayan pegado en %Depot%, realice estos cambios:

    - En %Depot%\MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPP.Targets, \Microsoft.Cpp.InvalidPlatforms.targets\\, \Microsoft.cppbuild.targets\\ y \Microsoft.CppCommon.targets\\, cambie cada instancia de

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         por

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll”.

         La nomenclatura anterior se basa en el almacenamiento de los ensamblados en la GAC.

    - En %Depot% \MSBuild\Microsoft.Cpp\v4.0\v110\Microsoft.CPPClean.Targets, cambie cada instancia de

         AssemblyName="Microsoft.Build.CppTasks.Common.v110, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

         por

         AssemblyFile="$(VCTargetsPath11)Microsoft.Build.CppTasks.Common.v110.dll”.

4. Cree un archivo .props (por ejemplo, Partner.AutoImports.props) y póngalo en la raíz de la carpeta que contiene los proyectos. Este archivo se usa para establecer las variables utilizadas por MSBuild para buscar diversos recursos. Si las variables no se establecen con este archivo, se establecen mediante otros archivos .props y .targets que dependen de las configuraciones del Registro. Puesto no vamos a establecer ninguna configuración del Registro, estas variables estarán vacías y se produciría un error de compilación. En su lugar, agregue esto a Partner.AutoImports.props:

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <!-- This file must be imported by all project files at the top of the project file. -->
    <Project ToolsVersion="4.0"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio 11.0\VC\</VCInstallDir_110>
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>
    </PropertyGroup>
    </Project>
    ```

5. En cada uno de los archivos de proyecto, agregue la siguiente línea al principio, después de la línea `<Project Default Targets…>`.

    ```
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>
    ```

6. Cambie el entorno de la línea de comandos de la manera siguiente:

    - Establezca Depot =*ubicación del directorio Depot creado en el paso 1*

    - Establezca path=%path%;*ubicación de MSBuild en el equipo*;%Depot%\Windows\System32;%Depot%\Windows\SysWOW64;%Depot%\Microsoft Visual Studio 11.0\Common7\IDE\

         Para la compilación nativa de 64 bits, apunte a MSBuild de 64 bits.

## <a name="see-also"></a>Otras referencias
 [Preparar un equipo de pruebas para ejecutar una](/cpp/windows/preparing-a-test-machine-to-run-a-debug-executable) [referencia de línea de comandos del](../msbuild/msbuild-command-line-reference.md) ejecutable de depuración
