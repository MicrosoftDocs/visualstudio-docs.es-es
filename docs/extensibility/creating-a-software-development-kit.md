---
title: Crear un Kit de desarrollo de Software | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 55b62ac0ac448023793f511389146ebb1b07da0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-software-development-kit"></a>Creación de un kit de desarrollo de software
Un kit de desarrollo de software (SDK) es un conjunto de API que puede hacer referencia como un solo elemento en Visual Studio. El **Administrador de referencias** cuadro de diálogo muestra todos los SDK que son relevantes para el proyecto. Cuando se agrega un SDK para un proyecto, la API están disponibles en Visual Studio.  
  
 Hay dos tipos de SDK:  
  
-   SDK de plataforma es componentes obligatorios para el desarrollo de aplicaciones para una plataforma. Por ejemplo, el [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK es necesario desarrollar [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicaciones.  
  
-   SDK de extensión es componentes opcionales que amplían una plataforma, pero no están obligatorio para el desarrollo de aplicaciones para esa plataforma.  
  
 Las secciones siguientes describen la infraestructura general de SDK y cómo crear un SDK de plataforma y un SDK de extensión.  
  
-   [SDK de plataforma](#PlatformSDKs)  
  
-   [SDK de extensión](#ExtensionSDKs)  
  
##  <a name="PlatformSDKs"></a> SDK de plataforma  
 SDK de plataforma necesarios para desarrollar aplicaciones para una plataforma. Por ejemplo, el [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK es necesario para desarrollar aplicaciones para [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
### <a name="installation"></a>Instalación  
 Todos los SDK de plataforma se instalará en HKLM\Software\Microsoft\Microsoft SDK\\\v [TPI] [TPV]\\ @InstallationFolder = [raíz del SDK]. En consecuencia, el [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK está instalado en HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1.  
  
### <a name="layout"></a>Diseño  
 SDK de plataforma tendrá el siguiente diseño:  
  
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
|Carpeta Referencias|Contiene los archivos binarios que contengan ninguna API que se pueden codificar en. Estos son los archivos de metadatos de Windows (WinMD) o ensamblados.|  
|DesignTime carpeta|Contiene archivos que son necesarias solo en el momento de previa-run/depuración. Estos figuran los documentos XML, bibliotecas, encabezados, archivos binarios de tiempo de diseño del cuadro de herramientas, artefactos de MSBuild y así sucesivamente<br /><br /> Documentos XML, idealmente, se colocaría en la carpeta \DesignTime, pero seguirán documentos XML para las referencias se coloquen junto con el archivo de referencia en Visual Studio. Por ejemplo, el documento XML para una referencia \References\\[configuración]\\[arch]\sample.dll será \References\\[configuración]\\[arch]\sample.xml y la versión localizada de ese documento será \References\\[configuración]\\[arch]\\[locale]\sample.xml.|  
|Carpeta de configuración|Puede haber solo tres carpetas: depurar, comercial y CommonConfiguration. Los autores SDK puedan colocar los archivos bajo CommonConfiguration si se debe usar el mismo conjunto de archivos del SDK, independientemente de la configuración que se aplicará a los consumidores SDK.|  
|Carpeta de arquitectura|Puede existir cualquier carpeta de la arquitectura admitida. Visual Studio es compatible con las arquitecturas siguientes: x86, x64, ARM así como neutral. Nota: Win32 que se asigna a x86 y AnyCPU asigna a neutro.<br /><br /> MSBuild busca solo en \CommonConfiguration\neutral SDK de plataforma.|  
|SDKManifest.xml|Este archivo describe cómo Visual Studio debe utilizar el SDK. Buscar en el manifiesto del SDK para [!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** el valor que muestra el Examinador de objetos en la lista de examinación.<br /><br /> **PlatformIdentity:** la existencia de este atributo indica a Visual Studio y MSBuild que el SDK es una plataforma de SDK y que las referencias agregadas de él no deben copiarse localmente.<br /><br /> **TargetFramework:** Visual Studio utiliza este atributo para asegurarse de que solo los proyectos que tienen como destino los mismos marcos como se especifica en el valor de este atributo puede consumir el SDK.<br /><br /> **MinVSVersion:** Visual Studio utiliza este atributo para utilizar solo el SDK que se aplican a él.<br /><br /> **Referencia:** este atributo debe especificarse para solo esas referencias que contienen controles. Para obtener información sobre cómo especificar si una referencia contiene controles, consulte a continuación.|  
  
##  <a name="ExtensionSDKs"></a> SDK de extensión  
 Las secciones siguientes describen lo que necesita hacer para implementar un SDK de extensión.  
  
### <a name="installation"></a>Instalación  
 SDK de extensión puede instalarse para un usuario específico o para todos los usuarios sin especificar una clave del registro. Para instalar un SDK para todos los usuarios, utilice la ruta de acceso siguiente:  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Para una instalación específica del usuario, utilice la ruta de acceso siguiente:  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Si desea utilizar una ubicación diferente, debe realizar una de estas dos cosas:  
  
1.  Especificarlo en una clave del registro:  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     y agregue una subclave (valor predeterminado) que tiene un valor de `<path to SDK><SDKName><SDKVersion>`.  
  
2.  Agregar la propiedad de MSBuild `SDKReferenceDirectoryRoot` al archivo de proyecto. El valor de esta propiedad es una lista de puntos y comas delimitada semi de directorios en el que residen los SDK de extensión que desea hacer referencia.  
  
### <a name="installation-layout"></a>Diseño de instalación  
 SDK de extensión tiene el siguiente diseño de instalación:  
  
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
  
1.  \\< SDKName\>\\< SDKVersion\>: el nombre y la versión de la extensión de SDK se deriva de los nombres de carpeta correspondiente en la ruta de acceso a la raíz del SDK. MSBuild usa esta identidad para encontrar el SDK en el disco y Visual Studio muestra esta identidad en el **propiedades** ventana y **Administrador de referencias** cuadro de diálogo.  
  
2.  En la carpeta referencias: los archivos binarios que contienen las API. Estas podrían ser ensamblados o archivos de metadatos de Windows (WinMD).  
  
3.  Carpeta Redist: los archivos que se necesitan para/depuración en tiempo de ejecución y deben obtener se empaquetan como parte de la aplicación del usuario. Todos los archivos binarios se deben colocar debajo \redist\\< config\>\\< arch\>, y los nombres de los binarios deben tener el formato siguiente para garantizar la unicidad:  **\<empresa >.\< producto >. \<propósito >. \<extensión >**. Por ejemplo, Microsoft.Cpp.Build.dll. Todos los archivos con nombres que podrían entrar en conflicto con nombres de archivo de otros SDK (por ejemplo, los archivos de javascript, css, pri, xaml, png y jpg) deben estar ubicados debajo \redist\\< config\>\\< arch\> \\< sdkname\>\ excepto los archivos que están asociados con XAML controla. Estos archivos deben estar ubicados debajo \redist\\< config\>\\< arch\>\\< componentname\>\\.  
  
4.  Carpeta DesignTime: los archivos que sean necesarios en solo previa-run/depuración tiempo y no debe empaquetarse como parte de la aplicación del usuario. Podría tratarse de documentos XML, bibliotecas, encabezados, archivos binarios de tiempo de diseño del cuadro de herramientas, artefactos de MSBuild y así sucesivamente. Los SDK que está pensado para uso de un proyecto nativo debe tener un *SDKName*archivo .props. A continuación muestra un ejemplo de este tipo de archivo.  
  
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
  
5.  Carpeta de configuración: tres subcarpetas: depuración, comercial y CommonConfiguration. Los autores SDK puedan colocar los archivos en CommonConfiguration cuando se debe usar el mismo conjunto de archivos del SDK, independientemente de la configuración de destino por el consumidor SDK.  
  
6.  Carpeta de arquitectura: se admiten las arquitecturas siguientes: x86, x64, ARM, neutral. Win32 se asigna a x86, y AnyCPU a neutro.  
  
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
  
1.  DisplayName: el valor que aparece en el Administrador de referencias, el Explorador de soluciones, Examinador de objetos y otras ubicaciones en la interfaz de usuario de Visual Studio.  
  
2.  ProductFamilyName: General SDK nombre del producto. Por ejemplo, el [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK denominado "Microsoft.WinJS.1.0" y "Microsoft.WinJS.2.0", que pertenecen a la misma familia de familia de productos SDK, "Microsoft.WinJS". Este atributo permite que Visual Studio y MSBuild realizar dicha conexión. Si no existe este atributo, el nombre de SDK se utiliza como el nombre de familia de productos.  
  
3.  FrameworkIdentity: especifica una dependencia en una o más bibliotecas de componentes de Windows que el valor de este atributo se coloca en el manifiesto de la aplicación consume. Este atributo solo es aplicable a las bibliotecas de componentes de Windows.  
  
4.  TargetFramework: especifica los SDK que están disponibles en el Administrador de referencias y el cuadro de herramientas. Esta es una lista delimitada por punto y coma de monikers de framework de destino, por ejemplo ".NET Framework, versión = v2.0; .NET Framework, versión = v4.5.1". Si se especifican varias versiones de la misma plataforma de destino, el Administrador de referencias usa la mínima versión especificada con propósitos de filtrado. Por ejemplo, si ".NET Framework, versión = v2.0; .NET Framework, versión = v4.5.1" se especifica, se usará el Administrador de referencias ".NET Framework, versión = v2.0". Si se especifica un perfil de framework de destino específico, solo dicho perfil se utilizará por el Administrador de referencias con propósitos de filtrado. Por ejemplo, si "Silverlight, versión = v4.0, perfil = WindowsPhone" se especifica, Administrador de referencias se filtra según el perfil de Windows Phone; un proyecto destinado a la versión completa de Silverlight 4.0 Framework no vea el SDK del Administrador de referencias.  
  
5.  MinVSVersion: la mínima versión de Visual Studio.  
  
6.  MaxPlatformVerson: La versión de la plataforma de destino máximo debe usarse para especificar las versiones de plataforma en la que el SDK de extensión no funcionará. Por ejemplo, se debe hacer referencia el paquete en tiempo de ejecución de Microsoft Visual C++ v11.0 solo por los proyectos de Windows 8. Por lo tanto, MaxPlatformVersion del proyecto de Windows 8 es 8.0. Esto significa que el Administrador de referencias filtra paquete de Microsoft Visual C++ en tiempo de ejecución para un proyecto de Windows 8.1 y MSBuild produce un error cuando un [!INCLUDE[win81](../debugger/includes/win81_md.md)] proyecto hace referencia a él. Nota: este elemento se admite a partir de [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)].  
  
7.  AppliesTo: especifica los SDK que están disponibles en el Administrador de referencias, especificando los tipos de proyecto de Visual Studio es aplicable. Se reconocen los nueve valores: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, administrado y nativo. Puede usar el autor del SDK y ("+"), o ("&#124;"), no ("!") operadores para especificar exactamente el ámbito de los tipos de proyecto que se aplican a lo SDK.  
  
     WindowsAppContainer identifica proyectos para [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicaciones.  
  
8.  SupportPrefer32Bit: Los valores admitidos son "True" y "False". El valor predeterminado es "True". Si el valor se establece en "False", MSBuild devuelve un error para [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] proyectos (o una advertencia para proyectos de escritorio) si el proyecto que hace referencia el SDK tiene Prefer32Bit habilitado. Para obtener más información sobre Prefer32Bit, consulte [Build Page, Project Designer (C#)](../ide/reference/build-page-project-designer-csharp.md) o [página compilación, Diseñador de proyectos (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures: lista de las arquitecturas que admite el SDK de separados con un punto y coma. MSBuild muestra una advertencia si no se admite la arquitectura del SDK de destino en el proyecto. Si no se especifica este atributo, MSBuild nunca muestra este tipo de advertencia.  
  
10. SupportsMultipleVersions: si este atributo se establece en **Error** o **advertencia**, MSBuild indica que el mismo proyecto no puede hacer referencia a varias versiones de la misma familia SDK. Si este atributo no existe o está establecido en **permitir**, MSBuild no muestra este tipo de error o advertencia.  
  
11. AppX: especifica la ruta de acceso a los paquetes de aplicación para la biblioteca de componentes de Windows en el disco. Este valor se pasa al componente de registro de la biblioteca de componentes de Windows durante la depuración local. La convención de nomenclatura para el nombre de archivo es  **\<empresa >.\< Producto >. \<Arquitectura >. \<Configuración >. \<Versión > AppX**. Configuración y la arquitectura son opcionales en el nombre del atributo y el valor del atributo si no se aplican a la biblioteca de componentes de Windows. Este valor solo es aplicable a las bibliotecas de componentes de Windows.  
  
12. CopyRedistToSubDirectory: Especifica que se deben copiar los archivos en la carpeta \redist relativa a la raíz del paquete de aplicación (es decir, el **ubicación del paquete** elegido en el Asistente para crear paquetes de aplicación) y raíz del diseño en tiempo de ejecución. La ubicación predeterminada es la raíz del paquete de aplicación y el diseño de F5.  
  
13. DependsOn: Una lista de identidades SDK que definen los SDK que depende este SDK. Este atributo aparece en el panel de detalles del Administrador de referencia.  
  
14. MoreInfo: dirección URL de la página web que proporciona ayuda y obtener más información. Este valor se usa en el vínculo más información en el panel derecho del Administrador de referencia.  
  
15. Tipo de registro: especifica el registro de archivo WinMD en el manifiesto de aplicación y es necesario para WinMD nativo, que tiene un archivo DLL de implementación correspondiente.  
  
16. Referencia del archivo: especificar para solo esas referencias que contienen controles o son archivos Winmd nativo. Para obtener información sobre cómo especificar si una referencia contiene controles, vea [especificar la ubicación de elementos de cuadro de herramientas](#ToolboxItems) a continuación.  
  
##  <a name="ToolboxItems"></a> Especificar la ubicación de los elementos de cuadro de herramientas  
 El elemento ToolBoxItems del esquema SDKManifest.xml especifica la categoría y ubicación de los elementos de cuadro de herramientas de plataforma y el SDK de extensión. Los ejemplos siguientes muestran cómo especificar distintas ubicaciones. Esto es aplicable a las referencias de WinMD o DLL.  
  
1.  Colocar controles en la categoría de cuadro de herramientas predeterminada.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2.  Colocar controles en un nombre de categoría determinado.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3.  Colocar controles en los nombres de categoría determinado.  
  
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
  
5.  Enumerar los controles específicos diferente en Blend y Visual Studio.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  Enumerar controles específicos y colocarlos bajo la ruta de acceso común Studio Visual o solo en todos los grupos de controles.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  Enumerar controles específicos y mostrar solo un conjunto específico de ChooseItems sin ellos está en el cuadro de herramientas.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Crear un SDK usando C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Tutorial: Crear un SDK usando C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)