---
title: Crear un Kit de desarrollo de Software | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a03611dcf06c5ecd7c2e638bdced6551bcb3a37
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998923"
---
# <a name="creating-a-software-development-kit"></a>Creación de un kit de desarrollo de software
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un kit de desarrollo de software (SDK) es una colección de API que puede hacer referencia como un solo elemento en Visual Studio. El **Administrador de referencias** cuadro de diálogo muestra todos los SDK que son pertinentes para el proyecto. Cuando se agrega un SDK a un proyecto, las API están disponibles en Visual Studio.  
  
 Hay dos tipos de SDK:  
  
- Los SDK de plataforma son componentes obligatorios para el desarrollo de aplicaciones para una plataforma. Por ejemplo, el [!INCLUDE[win81](../includes/win81-md.md)] SDK es necesario para desarrollar [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplicaciones.  
  
- SDK de extensión son componentes opcionales que amplían una plataforma pero no son obligatorios para el desarrollo de aplicaciones para esa plataforma.  
  
  Las secciones siguientes describen la infraestructura general de SDK y cómo crear un SDK de plataforma y un SDK de extensión.  
  
- [SDK de plataforma](#PlatformSDKs)  
  
- [SDK de extensión](#ExtensionSDKs)  
  
##  <a name="PlatformSDKs"></a> SDK de plataforma  
 Los SDK de plataforma necesarias para desarrollar aplicaciones para una plataforma. Por ejemplo, el [!INCLUDE[win81](../includes/win81-md.md)] SDK es necesario para desarrollar aplicaciones para [!INCLUDE[win81](../includes/win81-md.md)].  
  
### <a name="installation"></a>Instalación  
 Se instalarán todos los SDK de plataforma en HKLM\Software\Microsoft\Microsoft SDK\\[TPI] \v [TPV]\\ @InstallationFolder = [raíz del SDK]. En consecuencia, el [!INCLUDE[win81](../includes/win81-md.md)] SDK se instala en HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1.  
  
### <a name="layout"></a>Diseño  
 Los SDK de plataforma tendrá el siguiente diseño:  
  
```  
\[InstallationFolder root]  
            SDKManifest.xml  
            \References  
                  \[config]  
                        \[arch]  
            \DesignTime  
                  \[config]  
                        \[arch]  
```  
  
|Nodo|Descripción|  
|----------|-----------------|  
|Carpeta Referencias|Contiene archivos binarios que contienen las API que se pueden codificar en. Podría tratarse de ensamblados o archivos de metadatos de Windows (WinMD).|  
|Carpeta en tiempo de diseño|Contiene archivos que son necesarios solo en tiempo de pre-run o depuración. Podría tratarse documentos XML, bibliotecas, encabezados, archivos binarios en tiempo de diseño del cuadro de herramientas, los artefactos de MSBuild etc.<br /><br /> Documentos XML, idealmente, se colocarían en la carpeta \DesignTime, pero seguirán documentos XML para las referencias se coloquen junto con el archivo de referencia en Visual Studio. Por ejemplo, el documento XML para una referencia de \References\\[configuración]\\[arch]\sample.dll será \References\\[configuración]\\[arch]\sample.xml y la versión localizada de ese documento será \References\\[configuración]\\[arch]\\[locale]\sample.xml.|  
|Carpeta de configuración|Puede haber sólo tres carpetas: depuración, venta directa y CommonConfiguration. Los autores SDK pueden colocar los archivos bajo CommonConfiguration si debe utilizarse el mismo conjunto de archivos del SDK, independientemente de la configuración que se destinará al consumidor SDK.|  
|Carpeta de arquitectura|Puede existir cualquier carpeta de la arquitectura admitida. Visual Studio admite las siguientes arquitecturas: x86, x64, ARM y neutral. Nota: Win32 que se asigna a x86, y a neutro AnyCPU.<br /><br /> MSBuild busca solo en \CommonConfiguration\neutral de Platform SDK.|  
|SDKManifest.xml|Este archivo describe cómo Visual Studio debe utilizar el SDK. Examine el manifiesto del SDK para [!INCLUDE[win81](../includes/win81-md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** El valor que muestra el Examinador de objetos en la lista.<br /><br /> **PlatformIdentity:** La existencia de este atributo le indica a Visual Studio y MSBuild que el SDK es una plataforma de SDK y que las referencias agregadas a partir de él no deben copiarse localmente.<br /><br /> **TargetFramework:** Este atributo se usa Visual Studio para asegurarse de que solo proyectos que tienen como destino el mismos marcos tal como se especifica en el valor de este atributo puede consumir el SDK.<br /><br /> **MinVSVersion:** Este atributo se utiliza Visual Studio para consumir solo el SDK que se aplican a él.<br /><br /> **Referencia:** Este atributo debe especificarse para solo esas referencias que contienen controles. Para obtener información sobre cómo especificar si una referencia contiene controles, consulte a continuación.|  
  
##  <a name="ExtensionSDKs"></a> SDK de extensión  
 Las secciones siguientes describen lo que necesita hacer para implementar un SDK de extensión.  
  
### <a name="installation"></a>Instalación  
 SDK de extensión pueden instalarse para un usuario específico o para todos los usuarios sin especificar una clave del registro. Para instalar un SDK para todos los usuarios, utilice la ruta de acceso siguiente:  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Para una instalación específica del usuario, utilice la ruta de acceso siguiente:  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Si desea usar una ubicación diferente, debe hacer dos cosas:  
  
1.  Especifíquelo con una clave del registro:  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     y agregue una subclave (valor predeterminado) que tiene un valor de `<path to SDK><SDKName><SDKVersion>`.  
  
2.  Agregue la propiedad de MSBuild `SDKReferenceDirectoryRoot` al archivo de proyecto. El valor de esta propiedad es una lista delimitada por un signo de dos puntos de semi de directorios en el que residen los SDK de extensión que desea hacer referencia.  
  
### <a name="installation-layout"></a>Diseño de instalación  
 SDK de extensión tienen el siguiente diseño de instalación:  
  
```  
\<ExtensionSDKs root>  
           \<SDKName>  
                 \<SDKVersion>  
                        SDKManifest.xml  
                        \References  
                              \<config>  
                                    \<arch>  
                        \Redist  
                              \<config>  
                                    \<arch>  
                        \DesignTime  
                               \<config>  
                                     \<arch>  
  
```  
  
1.  \\< SDKName\>\\< SDKVersion\>: el nombre y la versión de la extensión de SDK se deriva de los nombres de carpeta correspondiente en la ruta de acceso a la raíz del SDK. MSBuild usa esta identidad para encontrar el SDK en el disco, y Visual Studio muestra esta identidad en el **propiedades** ventana y **Administrador de referencias** cuadro de diálogo.  
  
2.  Carpeta referencias: los archivos binarios que contienen las API. Podría tratarse de ensamblados o archivos de metadatos de Windows (WinMD).  
  
3.  Carpeta Redist: los archivos que son necesarios para el tiempo de ejecución o depuración y deberían obtener empaqueta como parte de la aplicación del usuario. Todos los archivos binarios deben colocarse debajo \redist\\< config\>\\< arch\>, y los nombres de los binarios deben tener el formato siguiente para garantizar la unicidad:  **\<compañía >.\< producto >. \<propósito >. \<extensión >**. Por ejemplo, Microsoft.Cpp.Build.dll. Todos los archivos con nombres que podrían entrar en conflicto con los nombres de archivo de otros SDK (por ejemplo, los archivos de javascript, css, pri, xaml, png y jpg) deben colocarse debajo \redist\\< config\>\\< arch\> \\< sdkname\>\, excepto los archivos que están asociados con XAML controla. Estos archivos deben colocarse debajo \redist\\< config\>\\< arch\>\\< componentname\>\\.  
  
4.  Carpeta DesignTime: los archivos que sean necesarios en solo pre-run o depuración de tiempo y no debe empaquetarse como parte de la aplicación del usuario. Podría tratarse de documentos XML, bibliotecas, encabezados, archivos binarios en tiempo de diseño del cuadro de herramientas, los artefactos de MSBuild y así sucesivamente. Los SDK que está pensado para el consumo de un proyecto nativo debe tener un *SDKName*archivo .props. A continuación muestra un ejemplo de este tipo de archivo.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>  
        <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>  
        <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>  
        <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>  
        <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>  
        <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>  
        <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>  
      </PropertyGroup>  
    </Project>  
  
    ```  
  
     Documentos de referencia XML se colocan junto con el archivo de referencia. Por ejemplo, el documento de referencia XML para el **\References\\< config\>\\< arch\>\sample.dll** ensamblado es **\References\\ < config\>\\< arch\>\sample.xml**, y es la versión localizada de ese documento **\References\\< config\>\\< arch\>\\< configuración regional\>\sample.xml**.  
  
5.  Carpeta de configuración: tres subcarpetas: Depuración, comercial y CommonConfiguration. Los autores SDK pueden colocar los archivos bajo CommonConfiguration cuando debe utilizarse el mismo conjunto de archivos del SDK, independientemente de la configuración de destino por el consumidor SDK.  
  
6.  Carpeta de arquitectura: se admiten las siguientes arquitecturas: x86, x64, ARM, neutral. Win32 que se asigna a x86, y a neutro AnyCPU.  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 Este archivo describe cómo Visual Studio debe utilizar el SDK. A continuación se muestra un ejemplo.  
  
```  
<FileList>  
DisplayName = "My SDK"  
ProductFamilyName = "My SDKs"  
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"  
MinVSVersion = "14.0"  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = "True"  
SupportedArchitectures = "x86;x64;ARM"  
SupportsMultipleVersions = "Error"  
CopyRedistToSubDirectory = "."  
DependsOn = "SDKB, version=2.0"  
MoreInfo = "http://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  
  
 La lista siguiente proporciona los elementos del archivo.  
  
1.  DisplayName: el valor que aparece en el Administrador de referencias, el Explorador de soluciones, Examinador de objetos y otras ubicaciones en la interfaz de usuario para Visual Studio.  
  
2.  ProductFamilyName: El nombre de producto general de SDK. Por ejemplo, el [!INCLUDE[winjs_long](../includes/winjs-long-md.md)] SDK se denomina "Microsoft.WinJS.1.0" y "Microsoft.WinJS.2.0", que pertenecen a la misma familia de la familia de productos SDK, "Microsoft.WinJS". Este atributo permite que Visual Studio y MSBuild para realizar esa conexión. Si este atributo no existe, el nombre de SDK se usa como el nombre de familia de productos.  
  
3.  FrameworkIdentity: especifica una dependencia en una o varias bibliotecas de componentes de Windows que el valor de este atributo se coloca en el manifiesto de la aplicación que lo consume. Este atributo solo es aplicable a las bibliotecas de componentes de Windows.  
  
4.  TargetFramework: especifica los SDK que están disponibles en el Administrador de referencias y el cuadro de herramientas. Esta es una lista delimitada por punto y coma de los monikers de la plataforma de destino, por ejemplo ".NET Framework, versión = v2.0; .NET Framework, versión = v4.5.1". Si se especifican varias versiones de la misma plataforma de destino, el Administrador de referencias usa la versión más baja especificada con propósitos de filtrado. Por ejemplo, si ".NET Framework, versión = v2.0; .NET Framework, versión = v4.5.1" se especifica, se usará el Administrador de referencias ".NET Framework, versión = v2.0". Si se especifica un perfil de framework de destino específica, solo ese perfil se usará el Administrador de referencias con propósitos de filtrado. Por ejemplo, cuando "Silverlight, versión = v4.0, perfil = Windows Phone" se especifica, Administrador de referencias se filtra según el perfil de Windows Phone; un proyecto destinado a la versión completa de Silverlight Framework 4.0 no ve el SDK del Administrador de referencias.  
  
5.  MinVSVersion: Visual Studio versión mínima.  
  
6.  MaxPlatformVerson: La versión de la plataforma de destino máximo debe usarse para especificar las versiones de plataforma en la que el SDK de extensión no funcionará. Por ejemplo, se debe hacer referencia el paquete de Microsoft Visual C++ Runtime v11.0 sólo los proyectos de Windows 8. Por lo tanto, MaxPlatformVersion del proyecto de Windows 8 es 8.0. Esto significa que el Administrador de referencias filtra paquete Microsoft Visual C++ en tiempo de ejecución para un proyecto de Windows 8.1 y MSBuild produce un error cuando un [!INCLUDE[win81](../includes/win81-md.md)] proyecto hace referencia a él. Nota: este elemento se admite a partir de [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].  
  
7.  AppliesTo: especifica los SDK que están disponibles en el Administrador de referencias mediante la especificación de tipos de proyecto de Visual Studio aplicables. Se reconocen los nueve valores: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, administrado y nativo. Puede usar el autor del SDK y ("+"), o ("&#124;"), no ("!") operadores especifican exactamente el ámbito de los tipos de proyecto que se aplican al SDK.  
  
     WindowsAppContainer identifica los proyectos de [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplicaciones.  
  
8.  SupportPrefer32Bit: Los valores admitidos son "True" y "False". El valor predeterminado es "True". Si el valor se establece en "False", MSBuild devuelve un error para [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] proyectos (o una advertencia para proyectos de escritorio) si el proyecto que hace referencia al SDK tiene Prefer32Bit habilitado. Para obtener más información acerca de Prefer32Bit, consulte [página compilación, Diseñador de proyectos (C#)](../ide/reference/build-page-project-designer-csharp.md) o [página compilación, Diseñador de proyectos (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures: un punto y coma lista delimitada por signos de arquitecturas que admite el SDK. MSBuild muestra una advertencia si no se admite la arquitectura del SDK de destino en el proyecto de consumo. Si no se especifica este atributo, MSBuild nunca muestra este tipo de advertencia.  
  
10. SupportsMultipleVersions: si este atributo se establece en **Error** o **advertencia**, MSBuild indica que el mismo proyecto no puede hacer referencia a varias versiones de la misma familia SDK. Si este atributo no existe o está establecido en **permitir**, MSBuild no mostrar este tipo de error o advertencia.  
  
11. AppX: especifica la ruta de acceso a los paquetes de aplicación para la biblioteca de componentes de Windows en el disco. Este valor se pasa al componente de registro de la biblioteca de componentes de Windows durante la depuración local. La convención de nomenclatura para el nombre de archivo es  **\<compañía >.\< Producto >. \<Arquitectura >. \<Configuration >. \<Versión > .appx**. Configuración y arquitectura son opcionales en el nombre del atributo y el valor del atributo si no se aplican a la biblioteca de componentes de Windows. Este valor solo es aplicable a las bibliotecas de componentes de Windows.  
  
12. CopyRedistToSubDirectory: especifica dónde se deben copiar los archivos en la carpeta \redist relativa a la raíz del paquete de aplicación (es decir, el **ubicación del paquete** elegido en el Asistente para crear paquetes de aplicación) y la raíz de diseño en tiempo de ejecución. La ubicación predeterminada es la raíz del paquete de aplicación y el diseño de F5.  
  
13. DependsOn: Una lista de identidades SDK que definen los SDK que depende este SDK. Este atributo aparece en el panel de detalles del Administrador de referencias.  
  
14. MoreInfo: la dirección URL a la página web que proporciona ayuda y obtener más información. Este valor se usa en el vínculo más información en el panel derecho del Administrador de referencias.  
  
15. Tipo de registro: especifica el registro de WinMD en el manifiesto de aplicación y es necesario para el archivo WinMD nativo, que tiene un archivo DLL de implementación homólogo.  
  
16. Referencia de archivo: puede especificar para solo esas referencias que contienen controles o son archivos Winmd nativos. Para obtener información sobre cómo especificar si una referencia contiene controles, vea [especificando la ubicación de los elementos del cuadro de herramientas](#ToolboxItems) a continuación.  
  
##  <a name="ToolboxItems"></a> Especificar la ubicación de los elementos de cuadro de herramientas  
 El elemento ToolBoxItems del esquema SDKManifest.xml especifica la categoría y ubicación de los elementos del cuadro de herramientas de plataforma y los SDK de extensión. Los ejemplos siguientes muestran cómo especificar ubicaciones diferentes. Esto es aplicable a las referencias WinMD o DLL.  
  
1.  Colocar controles en la categoría de cuadro de herramientas predeterminada.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2.  Colocar controles en un nombre de categoría en particular.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3.  Colocar controles en los nombres de categoría en particular.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Colocar controles en los nombres de categoría diferentes en Blend y Visual Studio.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Enumerar los controles concretos de manera diferente de Blend y Visual Studio.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  Enumerar controles específicos y colocarlos bajo la ruta de común de Visual Studio o solo en todos los grupos de controles.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  Controles específicos de enumerar y mostrar solo un conjunto específico de ChooseItems sin ellos que están en el cuadro de herramientas.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Creación de un SDK con C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Tutorial: Crear un SDK usando C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)
