---
title: Referencia del esquema de extensión VSIX 2.0 | Microsoft Docs
description: El esquema de extensión VSIX 2.0 define el formato de archivo para un archivo de manifiesto de implementación de VSIX, que describe el contenido de un paquete VSIX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 66393bbe6383fcc6cae942a3d7e86f1d701a9634
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905246"
---
# <a name="vsix-extension-schema-20-reference"></a>Referencia del esquema de extensión VSIX 2.0
Un archivo de manifiesto de implementación de VSIX describe el contenido de un paquete VSIX. El formato de archivo se rige por un esquema. La versión 2.0 de este esquema admite la adición de tipos y atributos personalizados.  El esquema del manifiesto es extensible. El cargador de manifiestos omite los elementos y atributos XML que no entiende.

> [!IMPORTANT]
> Visual Studio 2015 puede cargar archivos VSIX en los formatos Visual Studio 2010, Visual Studio 2012 o Visual Studio 2013 2015.

## <a name="package-manifest-schema"></a>Esquema del manifiesto del paquete
 El elemento raíz del archivo XML de manifiesto es `<PackageManifest>` . Tiene un único atributo `Version` , que es la versión del formato de manifiesto. Si se realizan cambios importantes en el formato, se cambia el formato de versión. En este artículo se describe la versión 2.0 del formato de manifiesto, que se especifica en el manifiesto estableciendo el atributo en el valor `Version` de Version="2.0".

### <a name="packagemanifest-element"></a>Elemento PackageManifest
 Dentro del `<PackageManifest>` elemento raíz, puede usar los siguientes elementos:

- `<Metadata>` - Metadatos e información de publicidad sobre el propio paquete. Solo se `Metadata` permite un elemento en el manifiesto.

- `<Installation>` - En esta sección se define cómo se puede instalar este paquete de extensión, incluidas las SKU de aplicación en las que se puede instalar. Solo se permite `Installation` un solo elemento en el manifiesto. Un manifiesto debe tener `Installation` un elemento o este paquete no se instalará en ninguna SKU.

- `<Dependencies>` - Aquí se define una lista opcional de dependencias para este paquete.

- `<Assets>` - Esta sección contiene todos los recursos incluidos en este paquete. Sin esta sección, este paquete no muestra ningún contenido.

- `<AnyElement>*` - El esquema de manifiesto es lo suficientemente flexible como para permitir cualquier otro elemento. Los elementos secundarios no reconocidos por el cargador de manifiestos se exponen en la API de Extension Manager como objetos XmlElement adicionales. Con estos elementos secundarios, las extensiones VSIX pueden definir datos adicionales en el archivo de manifiesto al que el código Visual Studio puede tener acceso en tiempo de ejecución. Vea [Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Elemento Metadata
 Esta sección son los metadatos sobre el paquete, su identidad y la información de publicidad. `<Metadata>` contiene los siguientes elementos:

- `<Identity>` : define la información de identificación de este paquete e incluye los atributos siguientes:

  - `Id` - Este atributo debe ser un identificador único para el paquete elegido por su autor. El nombre debe calificarse de la misma manera en que los tipos CLR tienen espacios de nombres: Company.Product.Feature.Name. El `Id` atributo está limitado a 100 caracteres.

  - `Version` : define la versión de este paquete y su contenido. Este atributo sigue el formato de control de versiones del ensamblado CLR: Major.Minor.Build.Revision (1.2.40308.00). Un paquete con un número de versión mayor se considera actualizaciones del paquete y se puede instalar a través de la versión instalada existente.

  - `Language` - Este atributo es el idioma predeterminado del paquete y corresponde a los datos textuales de este manifiesto. Este atributo sigue la convención de código de configuración regional de CLR para los ensamblados de recursos, por ejemplo: en-us, en, fr-fr. Puede especificar que `neutral` declare una extensión neutra del lenguaje que se ejecutará en cualquier versión de Visual Studio. El valor predeterminado es `neutral`.

  - `Publisher` - Este atributo identifica el publicador de este paquete, ya sea una empresa o un nombre individual. El `Publisher` atributo está limitado a 100 caracteres.

- `<DisplayName>` : este elemento especifica el nombre del paquete descriptivo que se muestra en la interfaz de usuario del Administrador de extensiones. El `DisplayName` contenido está limitado a 50 caracteres.

- `<Description>` - Este elemento opcional es una breve descripción del paquete y su contenido que se muestra en la interfaz de usuario del Administrador de extensiones. El `Description` contenido puede contener cualquier texto que desee, pero está limitado a 1000 caracteres.

- `<MoreInfo>` - Este elemento opcional es una dirección URL a una página en línea que contiene una descripción completa de este paquete. El protocolo debe especificarse como http.

- `<License>` - Este elemento opcional es una ruta de acceso relativa a un archivo de licencia (.txt, .rtf) incluido en el paquete.

- `<ReleaseNotes>` - Este elemento opcional es una ruta de acceso relativa a un archivo de notas de la versión incluido en el paquete (.txt, .rtf) o bien una dirección URL a un sitio web que muestra las notas de la versión.

- `<Icon>` - Este elemento opcional es una ruta de acceso relativa a un archivo de imagen (png, bmp, jpeg, ico) incluido en el paquete. La imagen de icono debe ser de 32 x 32 píxeles (o se verá reducido a ese tamaño) y aparecerá en la interfaz de usuario de listview. Si no `Icon` se especifica ningún elemento, la interfaz de usuario usa un valor predeterminado.

- `<PreviewImage>` - Este elemento opcional es una ruta de acceso relativa a un archivo de imagen (png, bmp, jpeg) incluido en el paquete. La imagen de vista previa debe ser de 200 x 200 píxeles y mostrarse en la interfaz de usuario de detalles. Si no `PreviewImage` se especifica ningún elemento, la interfaz de usuario usa un valor predeterminado.

- `<Tags>` - Este elemento opcional muestra etiquetas de texto delimitadas por punto y coma adicionales que se usan para las sugerencias de búsqueda. El `Tags` elemento está limitado a 100 caracteres.

- `<GettingStartedGuide>` - Este elemento opcional es una ruta de acceso relativa a un archivo HTML o una dirección URL a un sitio web que contiene información sobre cómo usar la extensión o el contenido dentro de este paquete. Esta guía se inicia como parte de una instalación.

- `<AnyElement>*` - El esquema de manifiesto es lo suficientemente flexible como para permitir cualquier otro elemento. Los elementos secundarios que no reconoce el cargador de manifiestos se exponen como una lista de objetos XmlElement. Con estos elementos secundarios, las extensiones VSIX pueden definir datos adicionales en el archivo de manifiesto y enumerarlos en tiempo de ejecución.

### <a name="installation-element"></a>Elemento Installation
 En esta sección se define cómo se puede instalar este paquete y las SKU de aplicación en las que se puede instalar. Esta sección contiene los atributos siguientes:

- `Experimental` - Establezca este atributo en true si tiene una extensión que está instalada actualmente para todos los usuarios, pero está desarrollando una versión actualizada en el mismo equipo. Por ejemplo, si ha instalado MyExtension 1.0 para todos los usuarios, pero quiere depurar MyExtension 2.0 en el mismo equipo, establezca Experimental="true". Este atributo está disponible en Visual Studio 2015 Update 1 y versiones posteriores.

- `Scope` - Este atributo puede tomar el valor "Global" o "ProductExtension":

  - "Global" especifica que la instalación no está en el ámbito de una SKU específica. Por ejemplo, este valor se usa cuando se instala un SDK de extensión.

  - "ProductExtension" especifica que se instala una extensión VSIX tradicional (versión 1.0) con ámbito de Visual Studio SKU individuales. Este es el valor predeterminado.

- `AllUsers` - Este atributo opcional especifica si este paquete se instalará para todos los usuarios. De forma predeterminada, este atributo es false, que especifica que el paquete es por usuario. (Cuando se establece este valor en true, el usuario que instala debe elevarse al nivel de privilegios administrativos para instalar el VSIX resultante.

- `InstalledByMsi` - Este atributo opcional especifica si un MSI instala este paquete. Los paquetes instalados por una MSI se instalan y administran mediante MSI (programas y características) y no por el administrador de extensiones Visual Studio.  De forma predeterminada, este atributo es false, que especifica que el paquete no está instalado por una MSI.

- `SystemComponent` - Este atributo opcional especifica si este paquete debe considerarse un componente del sistema. Los componentes del sistema no se muestran en la interfaz de usuario del Administrador de extensiones y no se pueden actualizar. De forma predeterminada, este atributo es false, que especifica que el paquete no es un componente del sistema.

- `AnyAttribute*` - El elemento acepta un conjunto de atributos de final abierto que se exponerán en tiempo de ejecución como `Installation` un diccionario de pares nombre-valor.

- `<InstallationTarget>` -Este elemento controla la ubicación donde el instalador de VSIX instala el paquete. Si el valor del atributo es "ProductExtension", el paquete debe tener como destino una SKU, que ha instalado un archivo de manifiesto como parte de su contenido para anunciar su disponibilidad en `Scope` las extensiones. El elemento tiene los atributos siguientes cuando el atributo tiene el valor explícito o `<InstallationTarget>` `Scope` predeterminado "ProductExtension":

  - `Id` : este atributo identifica el paquete.  El atributo sigue la convención de espacio de nombres: Company.Product.Feature.Name. El `Id` atributo solo puede contener caracteres alfanuméricos y está limitado a 100 caracteres. Valores esperados:

    - Microsoft.VisualStudio.IntegratedShell

    - Microsoft.VisualStudio.Pro

    - Microsoft.VisualStudio.Premium

    - Microsoft.VisualStudio.Ultimate

    - Microsoft.VisualStudio.VWDExpress

    - Microsoft.VisualStudio.VPDExpress

    - Microsoft.VisualStudio.VSWinExpress

    - Microsoft.VisualStudio.VSLS

    - My.Shell.App

  - `Version` - Este atributo especifica un intervalo de versiones con las versiones mínimas y máximas admitidas de esta SKU. Un paquete puede detallar las versiones de las SKU que admite. La notación del intervalo de versiones es [10.0 - 11.0], donde

    - [ : versión mínima inclusiva.

    - ] : versión máxima inclusiva.

    - ( : versión mínima exclusiva.

    - ) : versión máxima exclusiva.

    - Número de versión única: solo la versión especificada.

    > [!IMPORTANT]
    > La versión 2.0 del esquema VSIX se introdujo en Visual Studio 2012. Para usar este esquema, debe tener Visual Studio 2012 o posterior instalado en la máquina y usar el VSIXInstaller.exe que forma parte de ese producto. Puede tener como destino versiones anteriores de Visual Studio con una versión Visual Studio 2012 o posterior VSIXInstaller, pero solo con las versiones posteriores del instalador.

    Visual Studio números de versión de 2017 se pueden encontrar en Visual Studio [de compilación y fechas de lanzamiento.](../install/visual-studio-build-numbers-and-release-dates.md)

    Al expresar la versión para Visual Studio versiones de 2017, la versión secundaria siempre debe ser **0**. Por ejemplo, Visual Studio versión 15.3.26730.0 de 2017 debe expresarse como [15.0.26730.0,16.0). Esto solo es necesario para los Visual Studio 2017 y versiones posteriores.

  - `AnyAttribute*` - El elemento permite un conjunto de atributos de final abierto que se expone en tiempo de ejecución como `<InstallationTarget>` un diccionario de pares nombre-valor.

### <a name="dependencies-element"></a>Elemento Dependencies
 Este elemento contiene una lista de dependencias que declara este paquete. Si se especifica alguna dependencia, esos paquetes (identificados por `Id` sus ) se deben haber instalado antes.

- `<Dependency>` element: este elemento secundario tiene los siguientes atributos:

  - `Id` - Este atributo debe ser un identificador único para el paquete dependiente. Este valor de identidad debe coincidir `<Metadata><Identity>Id` con el atributo de un paquete del que depende este paquete. El `Id` atributo sigue la convención de espacio de nombres: Company.Product.Feature.Name. El atributo solo puede contener caracteres alfanuméricos y está limitado a 100 caracteres.

  - `Version` - Este atributo especifica un intervalo de versiones con las versiones mínimas y máximas admitidas de esta SKU. Un paquete puede detallar las versiones de las SKU que admite. La notación del intervalo de versiones es [12.0, 13.0], donde:

    - [ : versión mínima inclusiva.

    - ] : versión máxima inclusiva.

    - ( : versión mínima exclusiva.

    - ) : versión máxima exclusiva.

    - Número de versión única: solo la versión especificada.

  - `DisplayName` - Este atributo es el nombre para mostrar del paquete dependiente, que se usa en elementos de la interfaz de usuario, como cuadros de diálogo y mensajes de error. El atributo es opcional a menos que MSI instale el paquete dependiente.

  - `Location` - Este atributo opcional especifica la ruta de acceso relativa dentro de este VSIX a un paquete VSIX anidado o una dirección URL a la ubicación de descarga de la dependencia. Este atributo se usa para ayudar al usuario a encontrar el paquete de requisitos previos.

  - `AnyAttribute*` - El elemento acepta un conjunto de atributos de final abierto que se exponerán en tiempo de ejecución como `Dependency` un diccionario de pares nombre-valor.

### <a name="assets-element"></a>Elemento Assets
 Este elemento contiene una lista de etiquetas para cada extensión o elemento `<Asset>` de contenido que este paquete muestra.

- `<Asset>` - Este elemento contiene los siguientes atributos y elementos:

  - `Type` - Tipo de extensión o contenido representado por este elemento. Cada `<Asset>` elemento debe tener un único , pero varios elementos pueden tener el mismo `Type` `<Asset>` `Type` . Este atributo debe representarse como un nombre completo, según las convenciones de espacio de nombres. Los tipos conocidos son:

    1. Microsoft.VisualStudio.VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft.VisualStudio.ToolboxControl

    4. Microsoft.VisualStudio.Samples

    5. Microsoft.VisualStudio.ProjectTemplate

    6. Microsoft.VisualStudio.ItemTemplate

    7. Microsoft.VisualStudio.Assembly

       Puede crear sus propios tipos y darles nombres únicos. En tiempo de ejecución Visual Studio, el código puede enumerar y acceder a estos tipos personalizados a través de la API de Extension Manager.

  - `Path` : la ruta de acceso relativa al archivo o carpeta dentro del paquete que contiene el recurso.

  - `TargetVersion` : el intervalo de versiones al que se aplica el recurso especificado. Se usa para enviar varias versiones de recursos a diferentes versiones de Visual Studio. Requiere Visual Studio 2017.3 o posterior para tener efecto.

  - `AnyAttribute*` - Conjunto de atributos de apertura que se expone en tiempo de ejecución como diccionario de pares nombre-valor.

    `<AnyElement>*` - Se permite cualquier contenido estructurado entre una `<Asset>` etiqueta begin y end. Todos los elementos se exponen como una lista de objetos XmlElement. Las extensiones VSIX pueden definir metadatos específicos del tipo estructurado en el archivo de manifiesto y enumerarlos en tiempo de ejecución.

### <a name="sample-manifest"></a>Manifiesto de ejemplo

```xml
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

## <a name="see-also"></a>Consulta también

- [Enviar Visual Studio extensión](../extensibility/shipping-visual-studio-extensions.md)
