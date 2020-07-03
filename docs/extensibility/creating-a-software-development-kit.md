---
title: Creación de un kit de desarrollo de software | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61e547be5f240cafccc058eb7ea2249fd492554b
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904115"
---
# <a name="create-a-software-development-kit"></a>Crear un kit de desarrollo de software

Un kit de desarrollo de software (SDK) es una colección de API a las que se puede hacer referencia como un solo elemento en Visual Studio. En el cuadro de diálogo **Administrador de referencias** se muestran todos los SDK que son pertinentes para el proyecto. Al agregar un SDK a un proyecto, las API están disponibles en Visual Studio.

Hay dos tipos de SDK:

- Los SDK de la plataforma son componentes obligatorios para desarrollar aplicaciones para una plataforma. Por ejemplo, el [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK es necesario para desarrollar [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicaciones.

- Los SDK de extensión son componentes opcionales que amplían una plataforma pero no son obligatorios para desarrollar aplicaciones para esa plataforma.

En las secciones siguientes se describe la infraestructura general de los SDK y cómo crear un SDK de la plataforma y un SDK de extensión.

## <a name="platform-sdks"></a>SDK de la plataforma

Los SDK de la plataforma son necesarios para desarrollar aplicaciones para una plataforma. Por ejemplo, el [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK es necesario para desarrollar aplicaciones para [!INCLUDE[win81](../debugger/includes/win81_md.md)] .

### <a name="installation"></a>Instalación

Todos los SDK de la plataforma se instalarán en *HKLM\Software\Microsoft\Microsoft SDK \\ [TPI] \V [TPV] \\ @InstallationFolder = [raíz del SDK]*. En consecuencia, el [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK se instala en *HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1*.

### <a name="layout"></a>Layout

Los SDK de la plataforma tienen el siguiente diseño:

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

| Nodo | Descripción |
|------------------------| - |
| Carpeta *referencias* | Contiene archivos binarios que contienen las API que se pueden codificar. Podrían incluir archivos o ensamblados de metadatos de Windows (WinMD). |
| Carpeta *DesignTime* | Contiene archivos que solo son necesarios en el momento de la ejecución previa o la depuración. Esto podría incluir documentos XML, bibliotecas, encabezados, archivos binarios de tiempo de diseño del cuadro de herramientas, artefactos de MSBuild, etc.<br /><br /> Los documentos XML, idealmente, se colocarían en la carpeta *\DesignTime* , pero los documentos XML para las referencias seguirán colocados junto con el archivo de referencia en Visual Studio. Por ejemplo, el documento XML de una referencia<em>\References \\ [config] \\ [Arch] \sample.dll</em> será *\References \\ [config] \\ [Arch] \sample.xml*y la versión localizada de ese documento será *\References \\ [config] \\ [Arch] \\ [locale] \sample.xml*. |
| Carpeta de *configuración* | Solo puede haber tres carpetas: *Debug*, *Retail* y *CommonConfiguration*. Los autores de SDK pueden colocar sus archivos en *CommonConfiguration* si se debe consumir el mismo conjunto de archivos de SDK, independientemente de la configuración de destino del consumidor del SDK. |
| Carpeta de *arquitectura* | Puede existir cualquier carpeta de *arquitectura* compatible. Visual Studio admite las siguientes arquitecturas: x86, x64, ARM y neutral. Nota: Win32 se asigna a x86 y AnyCPU se asigna a neutral.<br /><br /> MSBuild solo busca en *\CommonConfiguration\neutral* para los SDK de plataforma. |
| *SDKManifest.xml* | Este archivo describe cómo debe usar Visual Studio el SDK. Busque el manifiesto del SDK para [!INCLUDE[win81](../debugger/includes/win81_md.md)] :<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** Valor que la Examinador de objetos muestra en la lista de exploración.<br /><br /> **PlatformIdentity:** La existencia de este atributo indica a Visual Studio y MSBuild que el SDK es un SDK de plataforma y que las referencias que se agregan desde él no se deben copiar localmente.<br /><br /> **TargetFramework:** Visual Studio usa este atributo para asegurarse de que solo los proyectos que tienen como destino los mismos marcos de trabajo que se especifican en el valor de este atributo pueden consumir el SDK.<br /><br /> **MinVSVersion:** Visual Studio usa este atributo para consumir solo los SDK que se aplican a él.<br /><br /> **Referencia:** Este atributo debe especificarse solo para las referencias que contienen controles. Para obtener información sobre cómo especificar si una referencia contiene controles, vea a continuación. |

## <a name="extension-sdks"></a>SDK de extensiones

En las secciones siguientes se describe lo que debe hacer para implementar un SDK de extensión.

### <a name="installation"></a>Instalación

Los SDK de extensión se pueden instalar para un usuario específico o para todos los usuarios sin especificar una clave del registro. Para instalar un SDK para todos los usuarios, use la siguiente ruta de acceso:

*% Archivos de programa%\Microsoft SDK \<target platform\> \v<número de versión de plataforma \> \ExtensionSDKs*

En el caso de una instalación específica del usuario, use la siguiente ruta de acceso:

*%USERPROFILE%\AppData\Local\Microsoft SDK \<target platform\> \v<número de versión de plataforma \> \ExtensionSDKs*

Si desea utilizar una ubicación diferente, debe realizar una de estas dos acciones:

1. Especifíquelo en una clave del registro:

     **HKLM\Software\Microsoft\Microsoft SDK \<target platform> \v<número de versión de plataforma \> \ExtensionSDKs\<SDKName>\<SDKVersion>**\

     y agregue una subclave (predeterminada) que tenga un valor de `<path to SDK><SDKName><SDKVersion>` .

2. Agregue la propiedad MSBuild `SDKReferenceDirectoryRoot` al archivo de proyecto. El valor de esta propiedad es una lista de directorios delimitada por punto y coma en la que residen los SDK de extensión a los que desea hacer referencia.

### <a name="installation-layout"></a>Diseño de instalación

Los SDK de extensión tienen el siguiente diseño de instalación:

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

1. \\<SDKName \> \\<SDKVersion \> : el nombre y la versión del SDK de extensión se derivan de los nombres de carpeta correspondientes en la ruta de acceso a la raíz del SDK. MSBuild usa esta identidad para buscar el SDK en el disco y Visual Studio muestra esta identidad en la ventana **propiedades** y el cuadro de diálogo **Administrador de referencias** .

2. Carpeta de *referencias* : archivos binarios que contienen las API. Podrían ser archivos o ensamblados de metadatos de Windows (WinMD).

3. Carpeta *Redist* : los archivos que se necesitan para el tiempo de ejecución o la depuración, y deben empaquetarse como parte de la aplicación del usuario. Todos los archivos binarios deben colocarse bajo *\redist \\<config \> \\<Arch \> *y los nombres binarios deben tener el formato siguiente para garantizar la exclusividad: *]* \<company> . \<product> \<purpose> \<extension> .. <em>. Por ejemplo, * Microsoft.Cpp.Build.dll</em>. Todos los archivos con nombres que pueden entrar en conflicto con los nombres de archivo de otros SDK (por ejemplo, JavaScript, CSS, PRI, XAML, PNG y JPG) se deben colocar bajo <em>\redist \\<config \> \\<Arch \> \\<sdkname, \> \* excepto los archivos que están asociados a controles XAML. Estos archivos se deben colocar bajo * \redist \\<config \> \\<Arch \> \\<componentName \> \\ </em>.

4. Carpeta *DesignTime* : los archivos que se necesitan solo en el tiempo de ejecución previa y depuración, y no se deben empaquetar como parte de la aplicación del usuario. Podrían ser documentos XML, bibliotecas, encabezados, archivos binarios en tiempo de diseño del cuadro de herramientas, artefactos de MSBuild, etc. Cualquier SDK destinado a su consumo por un proyecto nativo debe tener un archivo *SDKName. props* . A continuación se muestra un ejemplo de este tipo de archivo.

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

    Los documentos de referencia XML se colocan junto al archivo de referencia. Por ejemplo, el documento de referencia XML para *\References \\<config \> \\<Arch \>\sample.dll* Assembly es *\References \\<config \> \\<Arch \> *\sample.xmly la versión localizada de ese documento es *\References \\<config<de \> \\ \> \\ configuración regional \> *<.

5. Carpeta de *configuración* : tres subcarpetas: *Debug*, *Retail*y *CommonConfiguration*. Los autores de SDK pueden colocar sus archivos en *CommonConfiguration* cuando se debe consumir el mismo conjunto de archivos de SDK, independientemente de la configuración de destino del consumidor del SDK.

6. Carpeta de *arquitectura* : se admiten las siguientes arquitecturas: x86, x64, ARM, neutro. Win32 se asigna a x86 y AnyCPU se asigna a neutral.

### <a name="sdkmanifestxml"></a>SDKManifest.xml

En el archivo *SDKManifest.xml* se describe cómo debe usar Visual Studio el SDK. Este es un ejemplo:

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
MoreInfo = "https://msdn.microsoft.com/MySDK">
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />
<ToolboxItems VSCategory = "Toolbox.Default" />
</File>
</FileList>
```

La lista siguiente proporciona los elementos del archivo:

1. DisplayName: el valor que aparece en el administrador de referencias, Explorador de soluciones, Examinador de objetos y otras ubicaciones en la interfaz de usuario de Visual Studio.

2. ProductFamilyName: el nombre de producto del SDK general. Por ejemplo, el [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK se denomina "Microsoft. winjs. 1.0" y "Microsoft. winjs. 2.0", que pertenecen a la misma familia de productos de SDK, "Microsoft. winjs". Este atributo permite que Visual Studio y MSBuild realicen esa conexión. Si este atributo no existe, se utiliza el nombre del SDK como el nombre de la familia de productos.

3. FrameworkIdentity: especifica una dependencia en una o más bibliotecas de componentes de Windows. El valor de este atributo se coloca en el manifiesto de la aplicación de consumo. Este atributo solo es aplicable a las bibliotecas de componentes de Windows.

4. TargetFramework: especifica los SDK que están disponibles en el administrador de referencias y en el cuadro de herramientas. Se trata de una lista delimitada por signos de punto y coma de los monikers de la plataforma de destino, por ejemplo ".NET Framework, version = v 2.0; .NET Framework, version = v 4.5.1". Si se especifican varias versiones de la misma plataforma de destino, el administrador de referencias usa la versión especificada más baja para el filtrado. Por ejemplo, si se especifica ".NET Framework, version = v 2.0; .NET Framework, version = v 4.5.1", Reference Manager usará ".NET Framework, version = v 2.0". Si se especifica un perfil de plataforma de destino específico, el administrador de referencias solo usará ese perfil para el filtrado. Por ejemplo, si se especifica "Silverlight, version = v 4.0, Profile = WindowsPhone", el administrador de referencias filtra solo en el perfil de Windows Phone. un proyecto destinado a la versión completa de Silverlight 4,0 Framework no ve el SDK en el administrador de referencias.

5. MinVSVersion: la versión mínima de Visual Studio.

6. MaxPlatformVerson: se debe usar la versión máxima de la plataforma de destino para especificar las versiones de plataforma en las que el SDK de extensión no funcionará. Por ejemplo, solo los proyectos de Windows 8 deben hacer referencia al paquete de tiempo de ejecución de Microsoft Visual C++ v 11.0. Por lo tanto, el MaxPlatformVersion del proyecto de Windows 8 es 8,0. Esto significa que el administrador de referencias filtra Microsoft Visual C++ paquete en tiempo de ejecución para un proyecto de Windows 8.1 y MSBuild produce un error cuando un [!INCLUDE[win81](../debugger/includes/win81_md.md)] proyecto hace referencia a él. Nota: este elemento se admite a partir de [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] .

7. AppliesTo: especifica los SDK que están disponibles en el administrador de referencias mediante la especificación de los tipos de proyecto de Visual Studio aplicables. Se reconocen nueve valores: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Managed y nativo. El autor del SDK puede usar and ("+") o ("&#124;"), no ("!") operadores para especificar exactamente el ámbito de los tipos de proyecto que se aplican al SDK.

    WindowsAppContainer identifica los proyectos para las [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicaciones.

8. SupportPrefer32Bit: los valores admitidos son "true" y "false". El valor predeterminado es "true". Si el valor se establece en "false", MSBuild devuelve un error para [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] los proyectos (o una advertencia para los proyectos de escritorio) si el proyecto que hace referencia al SDK tiene Prefer32Bit habilitado. Para obtener más información sobre Prefer32Bit, vea página compilar [, diseñador de proyectos (C#)](../ide/reference/build-page-project-designer-csharp.md) o [Página compilar, diseñador de proyectos (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).

9. SupportedArchitectures: una lista delimitada por punto y coma de arquitecturas admitidas por el SDK. MSBuild muestra una advertencia si no se admite la arquitectura de SDK de destino en el proyecto de consumo. Si no se especifica este atributo, MSBuild nunca muestra este tipo de advertencia.

10. SupportsMultipleVersions: Si este atributo se establece en **error** o **ADVERTENCIA**, MSBuild indica que el mismo proyecto no puede hacer referencia a varias versiones de la misma familia de SDK. Si este atributo no existe o está establecido en **permitir**, MSBuild no muestra este tipo de error o advertencia.

11. AppX: especifica la ruta de acceso a los paquetes de la aplicación para la biblioteca de componentes de Windows en el disco. Este valor se pasa al componente de registro de la biblioteca de componentes de Windows durante la depuración local. La Convención de nomenclatura para el nombre de archivo es * \<Company> . \<Product> . \<Architecture> \<Configuration> \<Version> .. appx*. La configuración y la arquitectura son opcionales en el nombre del atributo y el valor del atributo si no se aplican a la biblioteca de componentes de Windows. Este valor solo es aplicable a las bibliotecas de componentes de Windows.

12. CopyRedistToSubDirectory: especifica dónde se deben copiar los archivos de la carpeta *\redist* en relación con la raíz del paquete de la aplicación (es decir, la **Ubicación del paquete** elegida en el Asistente para **crear paquetes de aplicaciones** ) y la raíz de diseño en tiempo de ejecución. La ubicación predeterminada es la raíz del paquete de la aplicación y el diseño **F5** .

13. DEPENDSON: una lista de identidades de SDK que definen los SDK de los que depende este SDK. Este atributo aparece en el panel de detalles del administrador de referencias.

14. MoreInfo: la dirección URL de la página web que proporciona ayuda y más información. Este valor se usa en el vínculo más información en el panel derecho del administrador de referencias.

15. Tipo de registro: especifica el registro de WinMD en el manifiesto de la aplicación y es necesario para WinMD nativo, que tiene un archivo DLL de implementación de homólogo.

16. Referencia de archivo: se especifica solo para las referencias que contienen controles o son archivos winmd nativas. Para obtener información sobre cómo especificar si una referencia contiene controles, vea [especificar la ubicación de los elementos del cuadro de herramientas](#ToolboxItems) a continuación.

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>Especificar la ubicación de los elementos del cuadro de herramientas

El elemento **ToolBoxItems** del esquema *SDKManifest.xml* especifica la categoría y la ubicación de los elementos del cuadro de herramientas en los SDK de la plataforma y de la extensión. En los siguientes ejemplos se muestra cómo especificar ubicaciones diferentes. Esto es aplicable a las referencias de WinMD o DLL.

1. Coloque los controles en la categoría predeterminada del cuadro de herramientas.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. Coloque los controles bajo un nombre de categoría determinado.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. Coloque los controles bajo nombres de categoría determinados.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. Coloque los controles bajo diferentes nombres de categoría en Blend y Visual Studio.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. Enumerar controles específicos de forma diferente en Blend y Visual Studio.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. Enumere los controles específicos y colóquelos en la ruta de acceso común de Visual Studio o solo en el grupo todos los controles.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. Enumerar controles específicos y mostrar solo un conjunto específico en ChooseItems sin que estén en el cuadro de herramientas.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>Vea también

- [Tutorial: crear un SDK con C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Tutorial: crear un SDK mediante C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Administración de referencias en un proyecto](../ide/managing-references-in-a-project.md)
