---
title: Referencia de esquema 2.0 de extensión VSIX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e295bc8c09f41c4c1c77b216a9d91d0644d2d24e
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388548"
---
# <a name="vsix-extension-schema-20-reference"></a>Referencia de esquema 2.0 de extensión VSIX
Un archivo de manifiesto de implementación de VSIX describe el contenido de un paquete VSIX. El formato de archivo se rige por un esquema. De este esquema de la versión 2.0 admite la adición de atributos y tipos personalizados.  El esquema del manifiesto es extensible. El cargador de manifiesto omite los elementos XML y atributos que no comprenda.  
  
> [!IMPORTANT]
>  Visual Studio 2015 puede cargar archivos VSIX en los formatos de Visual Studio 2010, Visual Studio 2012 o Visual Studio 2013.  
  
## <a name="package-manifest-schema"></a>Esquema del manifiesto de paquete  
 El elemento raíz del archivo de manifiesto XML es `<PackageManifest>`. Tiene un único atributo `Version`, que es la versión del formato de manifiesto. Si se realizan cambios importantes en el formato, se cambia el formato de versión. Este artículo describe la versión de formato de manifiesto 2.0, que se especifica en el manifiesto estableciendo el `Version` en el valor de versión = "2.0".  
  
### <a name="packagemanifest-element"></a>Elemento PackageManifest  
 Dentro de la `<PackageManifest>` elemento raíz, puede usar los siguientes elementos:  
  
-   `<Metadata>` -Metadatos e información de publicidad sobre el propio paquete. Solo un `Metadata` se admite el elemento en el manifiesto.  
  
-   `<Installation>` -Esta sección define la forma en que se puede instalar este paquete de extensión, incluidas las SKU de la aplicación que pueden instalar en. Una sola `Installation` se admite el elemento en el manifiesto. Debe tener un manifiesto un `Installation` elemento o este paquete no se instala en cualquier SKU.  
  
-   `<Dependencies>` -Una lista opcional de las dependencias de este paquete se definen aquí.  
  
-   `<Assets>` -Esta sección contiene todos los recursos contenidos en este paquete. Sin esta sección, este paquete no detectarán ningún contenido.  
  
-   `<AnyElement>*` -El esquema del manifiesto es lo suficientemente flexible como para permitir que cualquier otro elemento. Cualquier elemento secundario no reconocido por el cargador de manifiesto se expone en la API del Administrador de extensiones como objetos XmlElement adicionales. Las extensiones VSIX con estos elementos secundarios, pueden definir datos adicionales en el archivo de manifiesto que puede tener acceso código que se ejecuta en Visual Studio en tiempo de ejecución. Vea <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A> y <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>.  
  
### <a name="metadata-element"></a>Elemento de metadatos  
 En esta sección es los metadatos sobre el paquete, su identidad y anuncio de la información. `<Metadata>` contiene los siguientes elementos:  
  
-   `<Identity>` : Define la información de identificación para este paquete e incluye los siguientes atributos:  
  
    -   `Id` : Este atributo debe ser un identificador único para el paquete elegido por su autor. Se debe calificar el nombre de la misma manera que los tipos CLR son tiene espacio de nombres: Company.Product.Feature.Name. El `Id` atributo está limitado a 100 caracteres.  
  
    -   `Version` : Define la versión de este paquete y su contenido. Este atributo sigue el formato de control de versiones de ensamblado CLR: principal.secundaria.compilación.revisión (1.2.40308.00). Un paquete con un mayor número de versión se considera actualizaciones del paquete y puede instalarse a través de la versión instalada actualmente.  
  
    -   `Language` : Este atributo es el idioma predeterminado para el paquete y corresponde a los datos de texto de este manifiesto. Este atributo sigue la convención de código de configuración regional CLR para los ensamblados de recursos, por ejemplo: en-us, en, fr-fr. Puede especificar `neutral` para declarar una extensión independiente del idioma que se ejecutará en cualquier versión de Visual Studio. El valor predeterminado es `neutral`.  
  
    -   `Publisher` : Este atributo identifica el publicador de este paquete, una empresa o un nombre individual. El `Publisher` atributo está limitado a 100 caracteres.  
  
-   `<DisplayName>` : Este elemento especifica el nombre del paquete fácil de usar que se muestra en la UI del Administrador de extensiones. El `DisplayName` contenido está limitado a 50 caracteres.  
  
-   `<Description>` : Este elemento opcional es una breve descripción del paquete y su contenido se muestra en el Administrador de extensiones de UI. El `Description` contenido puede contener cualquier texto que desee, pero ha limitado a 1000 caracteres.  
  
-   `<MoreInfo>` : Este elemento opcional es una dirección URL a una página en línea que contiene una descripción completa de este paquete. El protocolo debe especificarse como http.  
  
-   `<License>` : Este elemento opcional es una ruta de acceso relativa a un archivo de licencia (.txt, .rtf) contenido en el paquete.  
  
-   `<ReleaseNotes>` : Este elemento opcional es cualquier ruta de acceso relativa a un archivo de notas de la versión contenido en el paquete (.txt, .rtf) o bien una dirección URL a un sitio Web que muestra las notas.  
  
-   `<Icon>` : Este elemento opcional es una ruta de acceso relativa a un archivo de imagen (png, bmp, jpeg, ico) contenido en el paquete. La imagen del icono debe ser 32 x 32 píxeles (o se reducirá a dicho tamaño) y aparece en la interfaz de usuario de la vista de lista. Si no hay ningún `Icon` elemento se especifica, la interfaz de usuario usa un valor predeterminado.  
  
-   `<PreviewImage>` : Este elemento opcional es una ruta de acceso relativa a un archivo de imagen (png, bmp, jpeg) contenido en el paquete. La imagen de vista previa debe ser 200 x 200 píxeles y se muestra en los detalles de la interfaz de usuario. Si no hay ningún `PreviewImage` elemento se especifica, la interfaz de usuario usa un valor predeterminado.  
  
-   `<Tags>` : Este elemento opcional muestra las etiquetas de texto delimitada por punto y coma adicional que se usan para sugerencias de búsqueda. El `Tags` elemento está limitado a 100 caracteres.  
  
-   `<GettingStartedGuide>` : Este elemento opcional es una ruta de acceso relativa a un archivo HTML o una dirección URL a un sitio Web que contiene información sobre cómo usar la extensión o el contenido dentro de este paquete. Esta guía se inicia como parte de una instalación.  
  
-   `<AnyElement>*` -El esquema del manifiesto es lo suficientemente flexible como para permitir que cualquier otro elemento. Los elementos secundarios que no son reconocidos por el cargador de manifiesto se exponen como una lista de objetos XmlElement. Con estos elementos secundarios, las extensiones VSIX pueden definir datos adicionales en el archivo de manifiesto y enumerarlos en tiempo de ejecución.  
  
### <a name="installation-element"></a>Elemento de la instalación  
 En esta sección se define la forma en que se puede instalar este paquete y las SKU de la aplicación que pueden instalar en. Esta sección contiene los siguientes atributos:  
  
-   `Experimental` : Establezca este atributo en true si tiene una extensión que actualmente está instalada para todos los usuarios, pero está desarrollando una versión actualizada en el mismo equipo. Por ejemplo, si ha instalado 1.0 MyExtension para todos los usuarios, pero desea depurar MyExtension 2.0 en el mismo equipo, establezca Experimental = "true". Este atributo está disponible en Visual Studio 2015 Update 1 y versiones posteriores.  
  
-   `Scope` : Este atributo puede tomar el valor "Global" o "ProductExtension":  
  
    -   "Global" Especifica que la instalación no está dirigida a una SKU específica. Por ejemplo, este valor se utiliza cuando se instala un SDK de extensión.  
  
    -   "ProductExtension" Especifica que una extensión VSIX (versión 1.0) tradicional con ámbito para cada SKU de Visual Studio está instalada. Este es el valor predeterminado.  
  
-   `AllUsers` : Este atributo opcional especifica si este paquete se instalará para todos los usuarios. De forma predeterminada, este atributo es false, que especifica que el paquete es por usuario. (Al establecer este valor en true, el usuario que instala debe elevar al nivel de privilegios administrativos para instalar VSIX resultante.  
  
-   `InstalledByMsi` : Este atributo opcional especifica si se instala este paquete de MSI. Los paquetes instalados por un archivo MSI se instalan y administrados por MSI (programas y características) y no mediante el Administrador de extensiones de Visual Studio.  De forma predeterminada, este atributo es false, que especifica que el paquete no está instalado en un archivo MSI.  
  
-   `SystemComponent` : Este atributo opcional especifica si este paquete se debe considerar un componente del sistema. Los componentes del sistema no se muestran en la UI del Administrador de extensiones y no se puede actualizar. De forma predeterminada, este atributo es false, que especifica que el paquete no es un componente del sistema.  
  
-   `AnyAttribute*` -El `Installation` elemento acepta un conjunto abierto de atributos que se expondrá en tiempo de ejecución como un diccionario de pares de nombre-valor.  
  
-   `<InstallationTarget>` : Este elemento controla la ubicación donde el instalador de VSIX instala el paquete. Si el valor de la `Scope` atributo es "ProductExtension" el paquete debe tener como destino una SKU, que tiene instalado un archivo de manifiesto como parte de su contenido para anunciar su disponibilidad a las extensiones. El `<InstallationTarget>` elemento tiene los siguientes atributos cuando el `Scope` atributo tiene la configuración explícita o el valor predeterminado "ProductExtension":  
  
    -   `Id` : Este atributo identifica el paquete.  El atributo sigue la convención de espacio de nombres: Company.Product.Feature.Name. El `Id` atributo puede contener solo caracteres alfanuméricos y está limitado a 100 caracteres. Valores esperados:  
  
        -   Microsoft.VisualStudio.IntegratedShell  
  
        -   Microsoft.VisualStudio.Pro  
  
        -   Microsoft.VisualStudio.Premium  
  
        -   Microsoft.VisualStudio.Ultimate  
  
        -   Microsoft.VisualStudio.VWDExpress  
  
        -   Microsoft.VisualStudio.VPDExpress  
  
        -   Microsoft.VisualStudio.VSWinExpress  
  
        -   Microsoft.VisualStudio.VSLS  
  
        -   My.Shell.App  
  
    -   `Version` : Este atributo especifica un intervalo de versiones con las versiones compatibles mínimas y máxima de esta SKU. Un paquete puede detallan las versiones de las SKU que admite. La notación de rango de versión es [10.0 y 11.0], donde  
  
        -   [-inclusivo de versión mínima.  
  
        -   ]-versión máximo inclusivo.  
  
        -   (-exclusivo de versión mínima.  
  
        -   ): versión máxima exclusivo.  
  
        -   Versión única # - solo la versión especificada.  
  
        > [!IMPORTANT]
        >  La versión 2.0 del esquema VSIX se introdujo en Visual Studio 2012. Para usar este esquema se debe tener Visual Studio 2012 o posterior instalado en el equipo y usa el VSIXInstaller.exe que forma parte de ese producto. Puede tener como destino versiones anteriores de Visual Studio con Visual Studio 2012 o posterior VSIXInstaller, pero solo mediante el uso de las versiones más recientes del instalador. 
        
        Números de versión de Visual Studio 2017 pueden encontrarse en [números de compilación de Visual Studio y fechas de lanzamiento](../install/visual-studio-build-numbers-and-release-dates.md).
        
        Cuando se expresa la versión para las versiones de Visual Studio 2017, versión secundaria debe ser siempre **0**. Por ejemplo, Visual Studio 2017 versión 15.3.26730.0 se debería expresar como [15.0.26730.0,16.0). Esto solo es necesario para los números de versión de Visual Studio 2017.
  
    -   `AnyAttribute*` -El `<InstallationTarget>` elemento permite a un conjunto abierto de atributos que se expone en tiempo de ejecución como un diccionario de pares de nombre-valor.  
  
### <a name="dependencies-element"></a>Elemento de dependencias  
 Este elemento contiene una lista de dependencias que declara este paquete. Si se especifican las dependencias, dichos paquetes (identificado por su `Id`) debe haberse instalado antes.  
  
-   `<Dependency>` elemento: este elemento secundario tiene los siguientes atributos:  
  
    -   `Id` : Este atributo debe ser un identificador único para el paquete dependiente. Este valor de identidad debe coincidir con el `<Metadata><Identity>Id` atributo de un paquete que depende este paquete. El `Id` atributo sigue la convención de espacio de nombres: Company.Product.Feature.Name. El atributo puede contener solo caracteres alfanuméricos y está limitado a 100 caracteres.  
  
    -   `Version` : Este atributo especifica un intervalo de versiones con las versiones compatibles mínimas y máxima de esta SKU. Un paquete puede detallan las versiones de las SKU que admite. Es la notación de rango de versión [12.0, 13.0], donde:  
  
        -   [-inclusivo de versión mínima.  
  
        -   ]-versión máximo inclusivo.  
  
        -   (-exclusivo de versión mínima.  
  
        -   ): versión máxima exclusivo.  
  
        -   Versión única # - solo la versión especificada.  
  
    -   `DisplayName` : Este atributo es el nombre para mostrar del paquete dependiente, que se usa en elementos de interfaz de usuario, como cuadros de diálogo y mensajes de error. El atributo es opcional, a menos que se instala el paquete dependiente de MSI.  
  
    -   `Location` : Este atributo opcional especifica la ruta de acceso relativa en este VSIX a un paquete VSIX anidado o una dirección URL a la ubicación de descarga de la dependencia. Este atributo se utiliza para ayudar al usuario busque el paquete de requisitos previos.  
  
    -   `AnyAttribute*` -El `Dependency` elemento acepta un conjunto abierto de atributos que se expondrá en tiempo de ejecución como un diccionario de pares de nombre-valor.  
  
### <a name="assets-element"></a>Elemento de activos  
 Este elemento contiene una lista de `<Asset>` etiquetas para cada elemento de extensión o contenido obtenidas por este paquete.  
  
- `<Asset>` : Este elemento contiene los atributos y los elementos siguientes:  
  
  - `Type` -Tipo de extensión o contenido representado por este elemento. Cada `<Asset>` elemento debe tener una sola `Type`, pero varios `<Asset>` elementos pueden tener el mismo `Type`. Este atributo se debe representar como un nombre completo, según las convenciones de espacio de nombres. Los tipos conocidos son:  
  
    1. Microsoft.VisualStudio.VsPackage  
  
    2. Microsoft.VisualStudio.MefComponent  
  
    3. Microsoft.VisualStudio.ToolboxControl  
  
    4. Microsoft.VisualStudio.Samples  
  
    5. Microsoft.VisualStudio.ProjectTemplate  
  
    6. Microsoft.VisualStudio.ItemTemplate  
  
    7. Microsoft.VisualStudio.Assembly  
  
       Puede crear sus propios tipos y asígneles los nombres únicos. En tiempo de ejecución dentro de Visual Studio, el código puede enumerar y tener acceso a estos tipos personalizados mediante la API del Administrador de extensiones.  
  
  - `Path` -la ruta de acceso relativa al archivo o carpeta dentro del paquete que contiene el recurso.  
    
  - `TargetVersion` -el intervalo de versiones a la que se aplica el recurso especificado. Utilizada para el envío de varias versiones de los recursos para diferentes versiones de Visual Studio. Requiere Visual Studio 2017.3 o posterior tener efecto.
  
  - `AnyAttribute*` -Un conjunto abierto de atributos que se expone en tiempo de ejecución como un diccionario de pares nombre-valor.  
  
     `<AnyElement>*` -Cualquier contenido estructurado no se permite entre un `<Asset>` comenzar y terminar la etiqueta. Todos los elementos se exponen como una lista de objetos XmlElement. Las extensiones VSIX pueden definir metadatos específicos del tipo estructurado en el archivo de manifiesto y enumerarlos en tiempo de ejecución.  
  
### <a name="sample-manifest"></a>Manifiesto de ejemplo  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
  <Metadata>  
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />  
    <DisplayName>Test Package</DisplayName>  
    <Description>Information about my package</Description>  
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>  
    <License>eula.rtf</License>  
    <ReleaseNotes>notes.txt</ReleaseNotes>  
    <Icon>Images\icon.png</Icon>  
    <PreviewImage>Images\preview.png</PreviewImage>  
  </Metadata>  
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />  
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />  
  </Assets>  
</PackageManifest>  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de Visual Studio de trasvase de registros](../extensibility/shipping-visual-studio-extensions.md)
