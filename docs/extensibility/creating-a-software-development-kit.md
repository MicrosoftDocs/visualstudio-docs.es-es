---
title: Creación de un kit de desarrollo de software Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7cf6cf092edf96280c566018231cc00d34c0994
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739592"
---
# <a name="create-a-software-development-kit"></a>Crear un kit de desarrollo de software

Un kit de desarrollo de software (SDK) es una colección de API a las que puede hacer referencia como un único elemento en Visual Studio. El cuadro de diálogo Administrador de **referencias** muestra todos los SDK que son relevantes para el proyecto. Al agregar un SDK a un proyecto, las API están disponibles en Visual Studio.

Hay dos tipos de SDK:

- Los SDK de plataforma son componentes obligatorios para desarrollar aplicaciones para una plataforma. Por ejemplo, [!INCLUDE[win81](../debugger/includes/win81_md.md)] el SDK [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] es necesario para desarrollar aplicaciones.

- Los SDK de extensión son componentes opcionales que extienden una plataforma pero no son obligatorios para desarrollar aplicaciones para esa plataforma.

En las secciones siguientes se describe la infraestructura general de los SDK y cómo crear un SDK de plataforma y un SDK de extensión.

## <a name="platform-sdks"></a>SDK de la plataforma

Los SDK de plataforma son necesarios para desarrollar aplicaciones para una plataforma. Por ejemplo, [!INCLUDE[win81](../debugger/includes/win81_md.md)] el SDK es [!INCLUDE[win81](../debugger/includes/win81_md.md)]necesario para desarrollar aplicaciones para .

### <a name="installation"></a>Instalación

Todos los SDK de la plataforma se instalarán en *HKLM,\\Software, Microsoft, Microsoft,\\ @InstallationFolder Microsoft, Sdk de Microsoft [TPI], v[TPV] y [raíz del SDK].* En consecuencia, [!INCLUDE[win81](../debugger/includes/win81_md.md)] el SDK se instala en *HKLM- Software , Microsoft SDKs , Windows , v8.1*.

### <a name="layout"></a>Diseño

Los SDK de plataforma tienen el siguiente diseño:

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
| *Carpeta Referencias* | Contiene archivos binarios que contienen API que se pueden codificar. Estos podrían incluir archivos o ensamblados de metadatos de Windows (WinMD). |
| *Carpeta DesignTime* | Contiene archivos que solo se necesitan en el momento de la ejecución previa/depuración. Estos podrían incluir documentos XML, bibliotecas, encabezados, binarios en tiempo de diseño de Toolbox, artefactos de MSBuild, etc.<br /><br /> Los documentos XML, idealmente, se colocarían en la carpeta *.DesignTime,* pero los documentos XML para las referencias seguirán colocándose junto al archivo de referencia en Visual Studio. Por ejemplo, el documento XML para una referencia<em>\\de referencia [config]\\[arch]-sample.dll</em> será *.references\\[config]\\[arch]-sample.xml*, y la versión localizada de ese documento será *"References\\[config]\\[arch] [arch]\\[locale]-sample.xml*. |
| *Carpeta de configuración* | Solo puede haber tres carpetas: *Depurar*, *Venta al público* y *CommonConfiguration*. Los autores del SDK pueden colocar sus archivos en *CommonConfiguration* si se debe consumir el mismo conjunto de archivos SDK, independientemente de la configuración a la que se destinará el consumidor del SDK. |
| *Carpeta de arquitectura* | Puede existir cualquier carpeta de *arquitectura* compatible. Visual Studio admite las siguientes arquitecturas: x86, x64, ARM y neutral. Nota: Win32 se asigna a x86 y AnyCPU se asigna a neutral.<br /><br /> MSBuild solo busca en *"CommonConfiguration" o "neutral"* para los SDK de plataforma. |
| *SDKManifest.xml* | Este archivo describe cómo Visual Studio debe consumir el SDK. Consulte el manifiesto [!INCLUDE[win81](../debugger/includes/win81_md.md)]del SDK para:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** Valor que muestra el Examinador de objetos en la lista Examinar.<br /><br /> **PlatformIdentity:** La existencia de este atributo indica a Visual Studio y MSBuild que el SDK es un SDK de plataforma y que las referencias agregadas desde él no se deben copiar localmente.<br /><br /> **TargetFramework:** Visual Studio usa este atributo para asegurarse de que solo los proyectos que tienen como destino los mismos marcos de trabajo especificados en el valor de este atributo pueden consumir el SDK.<br /><br /> **MinVSVersion:** Visual Studio usa este atributo para consumir solo los vales de servicio que se aplican a él.<br /><br /> **Referencia:** Este atributo debe especificarse solo para aquellas referencias que contienen controles. Para obtener información sobre cómo especificar si una referencia contiene controles, consulte a continuación. |

## <a name="extension-sdks"></a>SDK de extensiones

En las secciones siguientes se describe lo que debe hacer para implementar un SDK de extensión.

### <a name="installation"></a>Instalación

Los SDK de extensión se pueden instalar para un usuario específico o para todos los usuarios sin especificar una clave del Registro. Para instalar un SDK para todos los usuarios, utilice la siguiente ruta de acceso:

*%Archivos de programa%-Microsoft\<SDKs plataforma\>de\>destino .v<número de versión de la plataforma .*

Para una instalación específica del usuario, utilice la ruta de acceso siguiente:

*%USERPROFILE%-AppData-Local-Microsoft SDKs\<\>plataforma de destino\>.v<número de versión de la plataforma .*

Si desea utilizar una ubicación diferente, debe realizar una de estas dos acciones:

1. Especifique en una clave del Registro:

     **La\<plataforma de destino de los SDK de HKLM-Software-Microsoft-Microsoft>-v<número\>de versión de la plataforma>SDKName de ExtensionSDKs\<>\<SDKVersion>**\

     y agregue una subclave (predeterminada) `<path to SDK><SDKName><SDKVersion>`que tenga un valor de .

2. Agregue la propiedad `SDKReferenceDirectoryRoot` MSBuild al archivo de proyecto. El valor de esta propiedad es una lista delimitada por punto y coma de directorios en los que residen los SDK de extensión a los que desea hacer referencia.

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

1. \\<SDKName\> \\<\>SDKVersion : el nombre y la versión del SDK de extensión se derivan de los nombres de carpeta correspondientes en la ruta de acceso a la raíz del SDK. MSBuild usa esta identidad para buscar el SDK en el disco y Visual Studio muestra esta identidad en la ventana **Propiedades** y el cuadro de diálogo Administrador de **referencias.**

2. *Carpeta de referencias:* los archivos binarios que contienen las API. Podrían ser archivos o ensamblados de metadatos de Windows (WinMD).

3. *Carpeta Redist:* los archivos necesarios para el tiempo de ejecución/depuración y deben empaquetarse como parte de la aplicación del usuario. Todos los binarios deben colocarse debajo de la<*de\\ configuración\> \\<\>arco*, y los nombres binarios deben tener el siguiente formato para garantizar la unicidad: *]*\<> de la empresa. \<> de productos. \<propósito>. \<extensión><em>. Por ejemplo, *Microsoft.Cpp.Build.dll</em>. Todos los archivos con nombres que pueden colisionar con nombres de archivo de otros SDK (por ejemplo, archivos javascript, css, pri, xaml, png y jpg) deben colocarse debajo de los archivos <em>\\ de\> \\ \> \\ \> \* configuración de<de<configuración de los archivos de red (por ejemplo, javascript, css, pri, xaml, png y jpg) deben colocarse debajo de los archivos de<de configuración de los archivos de sdkname, excepto los archivos asociados con controles XAML. Estos archivos deben colocarse debajo\> \\ de\> \\ *-redist\>\\<config<arch<componentname</em>.

4. *Carpeta DesignTime:* los archivos que se necesitan solo en tiempo previo a la ejecución/depuración y no deben empaquetarse como parte de la aplicación del usuario. Estos podrían ser documentos XML, bibliotecas, encabezados, binarios en tiempo de diseño de la caja de herramientas, artefactos de MSBuild, etc. Cualquier SDK destinado al consumo por un proyecto nativo debe tener un archivo *SDKName.props.* A continuación se muestra un ejemplo de este tipo de archivo.

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

    Los documentos de referencia XML se colocan junto al archivo de referencia. Por ejemplo, el documento de referencia XML para el *\\ \> \\ \>* ensamblado de configuración de<de la<de<configuración de la configuración de la<de la configuración de la versión de archivo es de la<de la *\\ \> \\ \>* configuración de la configuración<archivo de la versión de ese documento y la versión localizada de ese documento es *"Referencias\\ \> \\<configuración<configuración<configuración\> \\ \>regional"* de la configuración regional de la versión de la<de la configuración regional de la dirección variable de la dirección base de la<de la configuración regional .

5. Carpeta de *configuración:* tres subcarpetas: *Depurar*, *Comercial*y *CommonConfiguration*. Los autores del SDK pueden colocar sus archivos en *CommonConfiguration* cuando se debe consumir el mismo conjunto de archivos SDK, independientemente de la configuración de destino del consumidor del SDK.

6. Carpeta de *arquitectura:* se admiten las siguientes arquitecturas: x86, x64, ARM, neutral. Win32 se asigna a x86 y AnyCPU se asigna a neutral.

### <a name="sdkmanifestxml"></a>SDKManifest.xml

El archivo *SDKManifest.xml* describe cómo Visual Studio debe consumir el SDK. A continuación se muestra un ejemplo:

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

1. DisplayName: el valor que aparece en el Administrador de referencias, el Explorador de soluciones, el Examinador de objetos y otras ubicaciones de la interfaz de usuario de Visual Studio.

2. ProductFamilyName: el nombre general del producto SDK. Por ejemplo, [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] el SDK se denomina "Microsoft.WinJS.1.0" y "Microsoft.WinJS.2.0", que pertenecen a la misma familia de productos SDK de la familia de productos, "Microsoft.WinJS". Este atributo permite que Visual Studio y MSBuild realicen esa conexión. Si este atributo no existe, el nombre del SDK se usa como nombre de familia del producto.

3. FrameworkIdentity: especifica una dependencia en una o varias bibliotecas de componentes de Windows. El valor de este atributo se coloca en el manifiesto de la aplicación consumidora. Este atributo solo es aplicable a las bibliotecas de componentes de Windows.

4. TargetFramework: especifica los ID que están disponibles en el Administrador de referencias y el cuadro de herramientas. Se trata de una lista delimitada por punto y coma de monikers de marco de trabajo de destino, por ejemplo ".NET Framework, versión v2.0; .NET Framework, versión .v4.5.1". Si se especifican varias versiones del mismo marco de destino, el Administrador de referencias utiliza la versión especificada más baja para fines de filtrado. Por ejemplo, si se especifica ".NET Framework, versión v2.0; .NET Framework, versión v4.5.1", el Administrador de referencias usará ".NET Framework, versión .v2.0". Si se especifica un perfil de marco de trabajo de destino específico, el Administrador de referencias solo usará ese perfil para fines de filtrado. Por ejemplo, cuando se especifica "Silverlight, version-v4.0, profile-WindowsPhone", el Administrador de referencias filtra solo el perfil de Windows Phone; un proyecto destinado a Silverlight 4.0 Framework completo no ve el SDK en el Administrador de referencias.

5. MinVSVersion: la versión mínima de Visual Studio.

6. MaxPlatformVerson: la versión máxima de la plataforma de destino debe usarse para especificar las versiones de plataforma en las que el SDK de extensión no funcionará. Por ejemplo, los proyectos de Windows 8 solo deben hacer referencia al paquete en tiempo de ejecución v11.0 de Microsoft Visual C++. Por lo tanto, MaxPlatformVersion del proyecto de Windows 8 es 8.0. Esto significa que el Administrador de referencias filtra Microsoft Visual C++ Runtime Package para un proyecto [!INCLUDE[win81](../debugger/includes/win81_md.md)] de Windows 8.1 y MSBuild produce un error cuando un proyecto hace referencia a él. Nota: este elemento se [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]admite a partir de .

7. AppliesTo: especifica los IDD que están disponibles en el Administrador de referencias especificando los tipos de proyecto de Visual Studio aplicables. Se reconocen nueve valores: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Managed y Native. El autor del SDK puede usar y ("+'), o ("&#124;"), no ("!") operadores para especificar exactamente el ámbito de los tipos de proyecto que se aplican al SDK.

    WindowsAppContainer identifica proyectos [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] para aplicaciones.

8. SupportPrefer32Bit: Los valores admitidos son "True" y "False". El valor predeterminado es "Verdadero". Si el valor se establece en "False", [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] MSBuild devuelve un error para los proyectos (o una advertencia para proyectos de escritorio) si el proyecto que hace referencia al SDK tiene Prefer32Bit habilitado. Para obtener más información acerca de Prefer32Bit, vea página Compilar, Diseñador de [proyectos (C)](../ide/reference/build-page-project-designer-csharp.md) o Compilar página, Diseñador de [proyectos (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).

9. SupportedArchitectures: una lista delimitada por punto y coma de las arquitecturas que admite el SDK. MSBuild muestra una advertencia si no se admite la arquitectura del SDK de destino en el proyecto de consumo. Si no se especifica este atributo, MSBuild nunca muestra este tipo de advertencia.

10. SupportsMultipleVersions: si este atributo se establece en **Error** o **Advertencia**, MSBuild indica que el mismo proyecto no puede hacer referencia a varias versiones de la misma familia de SDK. Si este atributo no existe o está establecido en **Permitir**, MSBuild no muestra este tipo de error o advertencia.

11. AppX: especifica la ruta de acceso a los paquetes de aplicación para la biblioteca de componentes de Windows en el disco. Este valor se pasa al componente de registro de la biblioteca de componentes de Windows durante la depuración local. La convención de nomenclatura para el nombre de archivo es * \<Company>.\<> del producto. \<> de arquitectura. \<> de configuración. \<Versión>.appx*. La configuración y la arquitectura son opcionales en el nombre del atributo y el valor del atributo si no se aplican a la biblioteca de componentes de Windows. Este valor solo es aplicable a las bibliotecas de componentes de Windows.

12. CopyRedistToSubDirectory: especifica dónde se deben copiar los archivos de la carpeta *.redist* en relación con la raíz del paquete de la aplicación (es decir, la ubicación del **paquete** elegida en el asistente **Crear paquete** de aplicación) y la raíz de diseño en tiempo de ejecución. La ubicación predeterminada es la raíz del paquete de la aplicación y el diseño **F5.**

13. DependsOn: una lista de identidades de SDK que definen los SDK de los que depende este SDK. Este atributo aparece en el panel de detalles del Administrador de referencias.

14. MoreInfo: la dirección URL de la página web que proporciona ayuda y más información. Este valor se utiliza en el vínculo Más información en el panel derecho del Administrador de referencias.

15. Tipo de registro: especifica el registro de WinMD en el manifiesto de la aplicación y es necesario para WinMD nativo, que tiene un archivo DLL de implementación homólogo.

16. Referencia de archivo: se especifica solo para las referencias que contienen controles o son WinMD nativos. Para obtener información sobre cómo especificar si una referencia contiene controles, consulte [Especificar la ubicación de los elementos del cuadro de herramientas](#ToolboxItems) a continuación.

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>Especifique la ubicación de los elementos de la caja de herramientas

El elemento **ToolBoxItems** del esquema *SDKManifest.xml* especifica la categoría y la ubicación de los elementos del cuadro de herramientas en los SDK de plataforma y extensión. En los ejemplos siguientes se muestra cómo especificar diferentes ubicaciones. Esto es aplicable a las referencias de WinMD o DLL.

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

3. Coloque los controles bajo nombres de categoría sin categorías particulares.

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

6. Enumerar controles específicos y colocarlos en la ruta de acceso común de Visual Studio o solo en el grupo todos los controles.

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

- [Tutorial: Crear un SDK con C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Tutorial: Crear un SDK con C o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Administrar referencias en un proyecto](../ide/managing-references-in-a-project.md)
