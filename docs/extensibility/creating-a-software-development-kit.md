---
title: "Crear un Kit de desarrollo de Software | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 54
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 54
---
# Crear un Kit de desarrollo de Software
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un kit de desarrollo de software (SDK) es un conjunto de API que se puede hacer referencia como un único elemento en Visual Studio. La **Administrador de referencias** cuadro de diálogo muestra todos los SDK que son relevantes para el proyecto. Cuando se agrega un SDK para un proyecto, la API están disponibles en Visual Studio.  
  
 Hay dos tipos de SDK:  
  
-   SDK de plataforma es componentes obligatorios para desarrollar aplicaciones para una plataforma. Por ejemplo, el [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK es necesario desarrollar [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicaciones.  
  
-   SDK de extensión son componentes opcionales que amplían una plataforma pero no son obligatorias para desarrollar aplicaciones para esa plataforma.  
  
 Las secciones siguientes describen la infraestructura general de SDK y cómo crear una plataforma de SDK y un SDK de extensión.  
  
-   [SDK de plataforma](#PlatformSDKs)  
  
-   [SDK de extensión](#ExtensionSDKs)  
  
##  <a name="a-nameplatformsdksa-platform-sdks"></a><a name="PlatformSDKs"></a> SDK de plataforma  
 SDK de plataforma necesarias para desarrollar aplicaciones para una plataforma. Por ejemplo, el [!INCLUDE[win81](../debugger/includes/win81_md.md)] se necesita el SDK para desarrollar aplicaciones para [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
### <a name="installation"></a>Instalación  
 Todos los platform SDK que se instalará en HKLM\Software\Microsoft\Microsoft SDK\\\v [TPI] [TPV]\\@InstallationFolder = [raíz SDK]. En consecuencia, el [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK instalado en HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1.  
  
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
|Carpeta Referencias|Contiene archivos binarios que contienen las API que pueden programarse contra. Podría tratarse de ensamblados o archivos de metadatos de Windows (WinMD).|  
|Carpeta DesignTime|Contiene archivos que se necesitan sólo en tiempo de pre-run y depurar. Estos podrían incluir documentos XML, bibliotecas, encabezados, archivos binarios de tiempo de diseño del cuadro de herramientas, artefactos de MSBuild y así sucesivamente<br /><br /> Documentos XML, idealmente, se colocarían en la carpeta \DesignTime, pero seguirán documentos XML para las referencias a colocarse junto con el archivo de referencia en Visual Studio. Por ejemplo, el documento XML para una referencia de \References\\[configuración]\\[arch]\sample.dll será \References\\[configuración]\\[arch]\sample.xml y la versión localizada de ese documento será \References\\[configuración]\\[arch]\\[locale]\sample.xml.|  
|Carpeta de configuración|Puede haber sólo tres carpetas: debug, comercial y CommonConfiguration. Los autores SDK pueden colocar los archivos bajo CommonConfiguration si debe utilizarse el mismo conjunto de archivos del SDK, independientemente de la configuración que se aplicará a los consumidores SDK.|  
|Carpeta de arquitectura|Puede haber cualquier carpeta arquitectura admitida. Visual Studio admite las arquitecturas siguientes: x86, x64, ARM y neutral. Nota: Win32 que se asigna a x86 y AnyCPU asigna a neutro.<br /><br /> MSBuild busca sólo bajo \CommonConfiguration\neutral de Platform SDK.|  
|SDKManifest.xml|Este archivo describe el modo en que Visual Studio debe utilizar el SDK de. Mire el manifiesto de SDK de [!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = “Windows”             PlatformIdentity = “Windows, version=8.1”             TargetFramework = “.NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1”             MinVSVersion = “14.0”>              <File Reference = “Windows.winmd”>                <ToolboxItems VSCategory = “Toolbox.Default” />             </File> </FileList>`<br /><br /> **DisplayName:** el valor que muestra el Examinador de objetos en la lista.<br /><br /> **PlatformIdentity:** la existencia de este atributo indica a Visual Studio y MSBuild que el SDK es una plataforma de SDK y que las referencias agregadas de él no deben copiarse localmente.<br /><br /> **TargetFramework:** Visual Studio utiliza este atributo para garantizar que sólo los proyectos de los marcos de la mismos según lo especificado en el valor de este atributo puede consumir el SDK.<br /><br /> **MinVSVersion:** Visual Studio utiliza este atributo para utilizar sólo el SDK que se aplican a él.<br /><br /> **Referencia:** este atributo debe especificarse para sólo esas referencias que contienen controles. Para obtener información sobre cómo especificar si una referencia contiene controles, consulte a continuación.|  
  
##  <a name="a-nameextensionsdksa-extension-sdks"></a><a name="ExtensionSDKs"></a> SDK de extensión  
 Las secciones siguientes describen lo que necesita para implementar una extensión de SDK.  
  
### <a name="installation"></a>Instalación  
 SDK de extensión se pueden instalar para un usuario específico o para todos los usuarios sin especificar una clave del registro. Para instalar un SDK para todos los usuarios, use la siguiente ruta:  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Para una instalación específica del usuario, utilice la siguiente ruta:  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Si desea utilizar una ubicación diferente, debe hacer dos cosas:  
  
1.  Especifíquelo en una clave del registro:  
  
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
  
1.  \\< SDKName\>\\< SDKVersion\>: el nombre y la versión de la extensión de SDK se deriva de los nombres de carpeta correspondiente en la ruta de acceso a la raíz SDK. MSBuild usa esta identidad para encontrar el SDK en el disco y Visual Studio muestra esta identidad en el **propiedades** ventana y **Administrador de referencias** cuadro de diálogo.  
  
2.  Carpeta de referencias: los archivos binarios que contienen las API. Puede tratarse de ensamblados o archivos de metadatos de Windows (WinMD).  
  
3.  Carpeta Redist: los archivos que son necesarios en tiempo de ejecución y depurar y deben obtener empaquetados como parte de la aplicación del usuario. Todos los archivos binarios deben colocarse bajo \redist\\< config\>\\< arch\>, y los nombres de los binarios deben tener el formato siguiente para garantizar su exclusividad: **\< compañía>. \< producto>. \< propósito>. \< extensión>**. Por ejemplo, Microsoft.Cpp.Build.dll. Todos los archivos con nombres que podrían entrar en conflicto con nombres de archivo del resto de SDK (por ejemplo, archivos javascript, css, pri, xaml, png y jpg) deben colocarse bajo \redist\\< config\>\\< arch\>\\< sdkname\>\ controla la excepción de los archivos que están asociados a XAML. Estos archivos deben colocarse bajo \redist\\< config\>\\< arch\>\\< componentname\>\\.  
  
4.  Carpeta DesignTime: los archivos necesarios en sólo pre-run y depurar tiempo y no debe empaquetarse como parte de la aplicación del usuario. Puede tratarse de documentos XML, bibliotecas, encabezados, archivos binarios de tiempo de diseño del cuadro de herramientas, artefactos de MSBuild y así sucesivamente. Los SDK que está pensado para el consumo de un proyecto nativo debe tener un *SDKName*archivo .props. A continuación muestra un ejemplo de este tipo de archivo.  
  
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
  
     Documentos de referencia XML se colocan junto con el archivo de referencia. Por ejemplo, el documento de referencia XML de la **\References\\< config\>\\< arch\>\sample.dll** ensamblado es **\References\\< config\>\\< arch\>\sample.xml**, y es la versión localizada de ese documento **\References\\< config\>\\< arch\>\\< configuración regional\>\sample.xml**.  
  
5.  Carpeta de configuración: tres subcarpetas: depurar, comercial y CommonConfiguration. Los autores de SDK pueden colocar los archivos bajo CommonConfiguration cuando se consume el mismo conjunto de archivos del SDK, independientemente de la configuración dirigida por el consumidor SDK.  
  
6.  Carpeta de arquitectura: se admiten las arquitecturas siguientes: x86, x64, ARM, neutral. Win32 se asigna a x86 y AnyCPU asigna a neutro.  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 Este archivo describe el modo en que Visual Studio debe utilizar el SDK de. A continuación se muestra un ejemplo.  
  
```  
<FileList>  
DisplayName = “My SDK”  
ProductFamilyName = “My SDKs”  
TargetFramework = “.NETCore, version=v4.5.1; .NETFramework, version=v4.5.1”  
MinVSVersion = “14.0”  
MaxPlatformVersion = "8.1"  
AppliesTo = "WindowsAppContainer + WindowsXAML"  
SupportPrefer32Bit = “True”  
SupportedArchitectures = “x86;x64;ARM”  
SupportsMultipleVersions = “Error”  
CopyRedistToSubDirectory = “.”  
DependsOn = “SDKB, version=2.0”  
MoreInfo = “http://msdn.microsoft.com/MySDK”>  
<File Reference = “MySDK.Sprint.winmd” Implementation = “XNASprintImpl.dll”>  
<Registration Type = “Flipper” Implementation = “XNASprintFlipperImpl.dll” />  
<Registration Type = “Flexer” Implementation = “XNASprintFlexerImpl.dll” />  
<ToolboxItems VSCategory = “Toolbox.Default” />  
</File>  
</FileList>  
```  
  
 La lista siguiente proporciona los elementos del archivo.  
  
1.  DisplayName: el valor que aparece en el Administrador de referencias, el Explorador de soluciones, Examinador de objetos y otras ubicaciones de la interfaz de usuario de Visual Studio.  
  
2.  ProductFamilyName: General SDK nombre del producto. Por ejemplo, el [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK denominado "Microsoft.WinJS.1.0" y "Microsoft.WinJS.2.0", que pertenecen a la misma familia de la familia de productos SDK, "Microsoft.WinJS". Este atributo permite que Visual Studio y MSBuild realizar dicha conexión. Si no existe este atributo, el nombre del SDK se utiliza como el nombre de la familia de productos.  
  
3.  FrameworkIdentity: especifica una dependencia en una o más bibliotecas de componentes de Windows que el valor de este atributo se coloca en el manifiesto de la aplicación consume. Este atributo solo es aplicable a las bibliotecas de componentes de Windows.  
  
4.  TargetFramework: especifica los SDK que están disponibles en el Administrador de referencias y el cuadro de herramientas. Esto es una lista delimitada por punto y coma de monikers de framework de destino, por ejemplo ".NET Framework, versión = v2.0; .NET Framework, versión = v4.5.1". Si se especifican varias versiones del mismo marco de destino, el Administrador de referencia usa la versión menor especificada con propósitos de filtrado. Por ejemplo, si ".NET Framework, versión = v2.0; .NET Framework, versión = v4.5.1" se especifica, se usará el Administrador de referencias ".NET Framework, versión = v2.0". Si se especifica un perfil de framework de destino específico, sólo ese perfil se usará el Administrador de referencias con propósitos de filtrado. Por ejemplo, si "Silverlight, versión = v4.0, perfil = Windows Phone" se especifica, los filtros de administrador de referencias en el perfil de Windows Phone; un proyecto destinado a la versión completa de Silverlight 4.0 Framework no vea el SDK del Administrador de referencias.  
  
5.  MinVSVersion: la mínima versión de Visual Studio.  
  
6.  MaxPlatformVerson: La versión de la plataforma de destino máximo debe usarse para especificar las versiones de la plataforma en la que el SDK de extensión no funcionará. Por ejemplo, se debe hacer referencia el v11.0 del paquete de Microsoft Visual C++ en tiempo de ejecución solo en proyectos de Windows 8. Por lo tanto, MaxPlatformVersion del proyecto de Windows 8 es 8.0. Esto significa que el Administrador de referencias filtra paquete de Microsoft Visual C++ en tiempo de ejecución para un proyecto de Windows 8.1 y MSBuild produce un error cuando un [!INCLUDE[win81](../debugger/includes/win81_md.md)] proyecto hace referencia a él. Nota: este elemento se admite a partir de [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)].  
  
7.  AppliesTo: especifica los SDK que están disponibles en el Administrador de referencias mediante la especificación de tipos de proyecto de Visual Studio es aplicables. Se reconocen los nueve valores: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, administrado y nativo. Puede usar el autor del SDK y ("+'), o ("&#124;"), no ("! ") operadores para especificar exactamente el ámbito de los tipos de proyecto que se aplican al SDK.  
  
     WindowsAppContainer identifica los proyectos para [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicaciones.  
  
8.  SupportPrefer32Bit: Los valores admitidos son "True" y "False". El valor predeterminado es "True". Si el valor se establece en "False", MSBuild devuelve un error para [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] proyectos (o una advertencia para proyectos de escritorio) si el proyecto que hace referencia el SDK tiene Prefer32Bit habilitado. Para obtener más información sobre Prefer32Bit, consulte [Build Page, Project Designer (C#)](../ide/reference/build-page-project-designer-csharp.md) o [página compilación, Diseñador de proyectos (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures: lista de arquitecturas que admite el SDK separados con un punto y coma. MSBuild genera una advertencia si no se admite la arquitectura del SDK de destino en el proyecto. Si no se especifica este atributo, MSBuild nunca muestra este tipo de advertencia.  
  
10. SupportsMultipleVersions: si este atributo se establece en **Error** o **Advertencia**, MSBuild indica que el mismo proyecto no puede hacer referencia a varias versiones de la misma familia SDK. Si este atributo no existe o está establecido en **Permitir**, MSBuild no muestra este tipo de error o advertencia.  
  
11. AppX: especifica la ruta de acceso a los paquetes de aplicación para la biblioteca de componentes de Windows en el disco. Este valor se pasa al componente de registro de la biblioteca de componentes de Windows durante la depuración local. La convención de nomenclatura para el nombre de archivo es **\< compañía>. \< producto>. \< arquitectura>. \< Configuration>. \< versión>.appx**. Configuración y arquitectura son opcionales en el nombre del atributo y el valor de atributo si no se aplican a la biblioteca de componentes de Windows. Este valor sólo es aplicable a las bibliotecas de componentes de Windows.  
  
12. CopyRedistToSubDirectory: especifica dónde deben copiar los archivos en la carpeta \redist en relación con la raíz del paquete de aplicación (es decir, la **ubicación de paquete** elegido en el Asistente para crear paquetes de aplicación) y la raíz de diseño en tiempo de ejecución. La ubicación predeterminada es la raíz del paquete de aplicación y el diseño de F5.  
  
13. DependsOn: Una lista de identidades SDK que definen los SDK que depende este SDK. Este atributo aparece en el panel de detalles del Administrador de referencias.  
  
14. Más información: la dirección URL a la página web que proporciona ayuda y más información. Este valor se utiliza en el vínculo más información en el panel derecho del Administrador de referencias.  
  
15. Tipo de registro: especifica el registro de WinMD en el manifiesto de aplicación y se requiere para WinMD nativo, que tiene un archivo DLL de implementación equivalente.  
  
16. Referencia del archivo: especificar para sólo las referencias que contienen controles o son archivos Winmd nativo. Para obtener información sobre cómo especificar si una referencia contiene controles, consulte [especificar la ubicación de elementos de cuadro de herramientas](#ToolboxItems) a continuación.  
  
##  <a name="a-nametoolboxitemsa-specifying-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a> Especificar la ubicación de los elementos de cuadro de herramientas  
 El elemento ToolBoxItems del esquema SDKManifest.xml especifica la categoría y ubicación de los elementos de cuadro de herramientas en la plataforma y el SDK de extensiones. Los ejemplos siguientes muestran cómo especificar distintas ubicaciones. Esto es aplicable a las referencias de WinMD o DLL.  
  
1.  Colocar controles en la categoría de cuadro de herramientas predeterminada.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.Default”/>       
    </File>  
    ```  
  
2.  Colocar controles en un nombre de categoría en particular.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory= “MyCategoryName”/>  
    </File>  
    ```  
  
3.  Colocar controles en los nombres de categoría en particular.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph”>  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = “Data”>  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Colocar controles en los nombres de categoría diferente en Blend y Visual Studio.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph” BlendCategory = “Controls/sample/Graph”>   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Enumerar los controles específicos en Blend y Visual Studio.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Graph”>  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = “Controls/sample/Graph”>  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  Enumerar los controles específicos y colocarlos en la ruta de acceso común de Studio Visual o solo en todos los grupos de controles.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.Common”>  
        <ToolboxItems />  
        <ToolboxItems VSCategory = “Toolbox.All”>  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  Enumerar controles específicos y mostrar únicamente un conjunto específico de ChooseItems sin ellas en el cuadro de herramientas.  
  
    ```  
    <File Reference = “sample.winmd”>  
        <ToolboxItems VSCategory = “Toolbox.ChooseItemsOnly”>  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Crear un SDK con C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Tutorial: Crear un SDK usando C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)