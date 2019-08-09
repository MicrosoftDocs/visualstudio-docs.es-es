---
title: Referencia del esquema de extensión VSIX 2,0 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b63f226b7aaadb851eab95f9b60f88f8f2be5ff1
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68869979"
---
# <a name="vsix-extension-schema-20-reference"></a>Referencia de esquema 2.0 de la extensión VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un archivo de manifiesto de implementación de VSIX describe el contenido de un paquete VSIX. El formato de archivo se rige por un esquema. La versión 2,0 de este esquema admite la adición de tipos y atributos personalizados.  El esquema del manifiesto es extensible. El cargador de manifiestos omite los elementos y atributos XML que no comprende.

> [!IMPORTANT]
> Visual Studio 2015 puede cargar archivos VSIX en los formatos de Visual Studio 2010, Visual Studio 2012 o Visual Studio 2013.

## <a name="package-manifest-schema"></a>Esquema del manifiesto del paquete
 El elemento raíz del archivo XML de manifiesto es `<PackageManifest>`, con un único atributo `Version`, que es la versión del formato del manifiesto. Si se realizan cambios importantes en el formato, se cambiará el formato de la versión. En este tema se describe la versión 2,0 del formato de manifiesto, que se especifica en `Version` el manifiesto estableciendo el atributo en el valor version = "2.0".

### <a name="packagemanifest-element"></a>Elemento PackageManifest
 En el `<PackageManifest>` elemento raíz, puede usar los siguientes elementos:

- `<Metadata>`-Metadatos e información de publicidad sobre el propio paquete. Solo se `Metadata` permite un elemento en el manifiesto.

- `<Installation>`: En esta sección se define la forma en que se puede instalar este paquete de extensión, incluidas las SKU de aplicación en las que se puede instalar. Solo se permite `Installation` un único elemento en el manifiesto. Un manifiesto debe tener un `Installation` elemento o este paquete no se instalará en ninguna SKU.

- `<Dependencies>`-Aquí se define una lista opcional de dependencias para este paquete.

- `<Assets>`: Esta sección contiene todos los recursos contenidos en este paquete. Sin esta sección, este paquete no mostrará ningún contenido.

- `<AnyElement>*`-El esquema del manifiesto es lo suficientemente flexible como para permitir cualquier otro elemento. Los elementos secundarios no reconocidos por el cargador de manifiestos se exponen en la API del administrador de extensiones como objetos XmlElement adicionales. Con estos elementos secundarios, las extensiones VSIX pueden definir datos adicionales en el archivo de manifiesto que el código que se ejecuta en Visual Studio puede tener acceso en tiempo de ejecución. Vea [AdditionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Elemento metadata
 Esta sección son los metadatos sobre el paquete, su identidad e información de publicidad. `<Metadata>`contiene los siguientes elementos:

- `<Identity>`: Define la información de identificación para este paquete e incluye los siguientes atributos:

  - `Id`: Este atributo debe ser un identificador único para el paquete elegido por su autor. El nombre se debe calificar de la misma manera que los tipos CLR: Company.Product.Feature.Name. El `Id` atributo está limitado a 100 caracteres.

  - `Version`: Define la versión de este paquete y su contenido. Este atributo sigue el formato de control de versiones de ensamblado de CLR: Major. minor. Build. revision (1.2.40308.00). Un paquete con un número de versión superior se considera actualizaciones para el paquete y se puede instalar con la versión instalada existente.

  - `Language`: Este atributo es el idioma predeterminado del paquete y corresponde a los datos de texto de este manifiesto. Este atributo sigue la Convención de código de configuración regional de CLR para los ensamblados de recursos, por ejemplo: en-US, en, fr-fr. Puede especificar `neutral` para declarar una extensión independiente del lenguaje que se ejecutará en cualquier versión de Visual Studio. El valor predeterminado es `neutral`.

  - `Publisher`: Este atributo identifica el publicador de este paquete, ya sea una empresa o un nombre individual. El `Publisher` atributo está limitado a 100 caracteres.

- `<DisplayName>`: Este elemento especifica el nombre del paquete descriptivo que se muestra en la interfaz de usuario del administrador de extensiones. El `DisplayName` contenido está limitado a 100 caracteres.

- `<Description>`: Este elemento opcional es una breve descripción del paquete y su contenido que se muestra en la interfaz de usuario del administrador de extensiones. El `Description` contenido puede contener cualquier texto que desee, pero está limitado a 1000 caracteres.

- `<MoreInfo>`: Este elemento opcional es una dirección URL a una página en línea que contiene una descripción completa de este paquete. El protocolo debe especificarse como http.

- `<License>`: Este elemento opcional es una ruta de acceso relativa a un archivo de licencia (. txt,. rtf) contenido en el paquete.

- `<ReleaseNotes>`: Este elemento opcional es una ruta de acceso relativa a un archivo de notas de la versión contenida en el paquete (. txt,. rtf), o bien una dirección URL a un sitio web que muestra las notas de la versión.

- `<Icon>`: Este elemento opcional es una ruta de acceso relativa a un archivo de imagen (PNG, BMP, JPEG, ICO) incluido en el paquete. La imagen del icono debe ser de 32 x 32 píxeles (o se reducirá a ese tamaño) y aparece en la interfaz de usuario de ListView. Si no `Icon` se especifica ningún elemento, la interfaz de usuario usa un valor predeterminado.

- `<PreviewImage>`: Este elemento opcional es una ruta de acceso relativa a un archivo de imagen (PNG, BMP, JPEG) incluido en el paquete. La imagen de vista previa debe ser 200 x 200 píxeles y mostrarse en la interfaz de usuario de detalles. Si no `PreviewImage` se especifica ningún elemento, la interfaz de usuario usa un valor predeterminado.

- `<Tags>`: Este elemento opcional muestra etiquetas de texto adicionales delimitadas por punto y coma que se usan para las sugerencias de búsqueda. El `Tags` elemento está limitado a 100 caracteres.

- `<GettingStartedGuide>`: Este elemento opcional es una ruta de acceso relativa a un archivo HTML o una dirección URL a un sitio web que contiene información sobre cómo usar la extensión o el contenido de este paquete. Esta guía se inicia como parte de una instalación de.

- `<AnyElement>*`-El esquema del manifiesto es lo suficientemente flexible como para permitir cualquier otro elemento. Los elementos secundarios que no reconoce el cargador de manifiestos se exponen como una lista de objetos XmlElement. Con estos elementos secundarios, las extensiones VSIX pueden definir datos adicionales en el archivo de manifiesto y enumerarlos en tiempo de ejecución.

### <a name="installation-element"></a>Elemento de instalación
 En esta sección se define la forma en que se puede instalar este paquete y las SKU de aplicación en las que se puede instalar. Esta sección contiene los siguientes atributos:

- `Experimental`: Establezca este atributo en true si tiene una extensión instalada actualmente para todos los usuarios, pero está desarrollando una versión actualizada en el mismo equipo. Por ejemplo, si ha instalado la extensión 1,0 para todos los usuarios, pero desea depurar la extensión @ 2,0 en el mismo equipo, establezca experimental = "true". Este atributo está disponible en la actualización 1 de Visual Studio 2015 y versiones posteriores.

- `Scope`: Este atributo puede tomar el valor "global" o "ProductExtension":

  - "Global" especifica que la instalación no está en el ámbito de una SKU específica. Por ejemplo, este valor se usa cuando se instala un SDK de extensión.

  - "ProductExtension" especifica que se instala una extensión VSIX tradicional (versión 1,0) cuyo ámbito es una SKU de Visual Studio individual. Este es el valor predeterminado.

- `AllUsers`: Este atributo opcional Especifica si este paquete se instalará para todos los usuarios. De forma predeterminada, este atributo es false, que especifica que el paquete es por usuario. (Cuando este valor se establece en true, el usuario que instala debe elevarse al nivel de privilegios administrativos para instalar el VSIX resultante.

- `InstalledByMsi`: Este atributo opcional Especifica si este paquete se instala mediante un MSI. Los paquetes instalados por un MSI se instalan y administran mediante MSI (programas y características) y no por el administrador de extensiones de Visual Studio.  De forma predeterminada, este atributo es false, que especifica que el paquete no se instala mediante un MSI.

- `SystemComponent`: Este atributo opcional Especifica si este paquete se debe considerar un componente del sistema. Los componentes del sistema no se muestran en la interfaz de usuario del administrador de extensiones y no se pueden actualizar. De forma predeterminada, este atributo es false, que especifica que el paquete no es un componente del sistema.

- `AnyAttribute*`: El `Installation` elemento acepta un conjunto abierto de atributos que se expondrán en tiempo de ejecución como un diccionario de pares nombre-valor.

- `<InstallationTarget>`: Este elemento controla la ubicación donde el instalador de VSIX instala el paquete. Si el valor del `Scope` atributo es "ProductExtension", el paquete debe tener como destino una SKU que tenga instalado un archivo de manifiesto como parte de su contenido para anunciar su disponibilidad en las extensiones. El `<InstallationTarget>` elemento tiene los atributos siguientes cuando el `Scope` atributo tiene el valor explícito o predeterminado "ProductExtension":

  - `Id`: Este atributo identifica el paquete.  El atributo sigue la Convención de espacio de nombres: Company.Product.Feature.Name. El `Id` atributo solo puede contener caracteres alfanuméricos y está limitado a 100 caracteres. Valores esperados:

    - Microsoft.VisualStudio.IntegratedShell

    - Microsoft.VisualStudio.Pro

    - Microsoft.VisualStudio.Premium

    - Microsoft.VisualStudio.Ultimate

    - Microsoft.VisualStudio.VWDExpress

    - Microsoft.VisualStudio.VPDExpress

    - Microsoft.VisualStudio.VSWinExpress

    - Microsoft.VisualStudio.VSLS

    - My. Shell. app

  - `Version`: Este atributo especifica un intervalo de versiones con las versiones mínima y máxima admitidas de esta SKU. Un paquete puede detallar las versiones de las SKU que admite. La notación de intervalo de versión es [10,0 – 11,0], donde

    - [– versión mínima inclusive.

    - ]: versión máxima incluida.

    - (-versión mínima exclusiva.

    - ): versión máxima exclusiva.

    - Versión única #: solo la versión especificada.

    > [!IMPORTANT]
    > La versión 2,0 del esquema VSIX se presentó en Visual Studio 2012. Para usar este esquema, debe tener Visual Studio 2012 o posterior instalado en la máquina y usar el archivo VSIXInstaller. exe que forma parte de ese producto. Puede tener como destino versiones anteriores de Visual Studio con un VSIXInstaller de Visual Studio 2012 o posterior, pero solo con las versiones posteriores del instalador.

  - `AnyAttribute*`: El `<InstallationTarget>` elemento permite un conjunto abierto de atributos que se expondrán en tiempo de ejecución como un diccionario de pares nombre-valor.

### <a name="dependencies-element"></a>Elemento Dependencies
 Este elemento contiene una lista de dependencias que este paquete declara. Si se especifica alguna dependencia, los paquetes (identificados por su `Id`) se deben haber instalado antes.

- `<Dependency>`elemento: este elemento secundario tiene los siguientes atributos:

  - `Id`: Este atributo debe ser un identificador único para el paquete dependiente. Este valor de identidad debe coincidir con el `<Metadata><Identity>Id` atributo de un paquete del que depende este paquete. El `Id` atributo sigue la Convención de espacio de nombres: Company.Product.Feature.Name. El atributo solo puede contener caracteres alfanuméricos y está limitado a 100 caracteres.

  - `Version`: Este atributo especifica un intervalo de versiones con las versiones mínima y máxima admitidas de esta SKU. Un paquete puede detallar las versiones de las SKU que admite. La notación de intervalo de versión es [12,0, 13,0], donde:

    - [– versión mínima inclusive.

    - ]: versión máxima incluida.

    - (-versión mínima exclusiva.

    - ): versión máxima exclusiva.

    - Versión única #: solo la versión especificada.

  - `DisplayName`: Este atributo es el nombre para mostrar del paquete dependiente que se usa en los elementos de la interfaz de usuario, como los cuadros de diálogo y los mensajes de error. El atributo es opcional a menos que MSI Instale el paquete dependiente.

  - `Location`: Este atributo opcional especifica la ruta de acceso relativa dentro de esta VSIX a un paquete VSIX anidado o una dirección URL a la ubicación de descarga de la dependencia. Este atributo se usa para ayudar al usuario a encontrar el paquete de requisitos previos.

  - `AnyAttribute*`: El `Dependency` elemento acepta un conjunto abierto de atributos que se expondrán en tiempo de ejecución como un diccionario de pares nombre-valor.

### <a name="assets-element"></a>Elemento Assets
 Este elemento contiene una lista de `<Asset>` etiquetas para cada extensión o elemento de contenido expuesta por este paquete.

- `<Asset>`: Este elemento contiene los siguientes atributos y elementos:

  - `Type`: Es el tipo de extensión o contenido representado por este elemento. Cada `<Asset>` elemento debe tener un único `Type`, pero varios `<Asset>` elementos pueden tener el mismo `Type`. Este atributo se debe representar como un nombre completo, de acuerdo con las convenciones de espacio de nombres. Los tipos conocidos son:

    1. Microsoft.VisualStudio.VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft.VisualStudio.ToolboxControl

    4. Microsoft.VisualStudio.Samples

    5. Microsoft.VisualStudio.ProjectTemplate

    6. Microsoft.VisualStudio.ItemTemplate

    7. Microsoft.VisualStudio.Assembly

       Puede crear sus propios tipos y asignarles nombres únicos. En tiempo de ejecución dentro de Visual Studio, el código puede enumerar y tener acceso a estos tipos personalizados a través de la API del administrador de extensiones.

  - Ruta de acceso: la ruta de acceso relativa al archivo o la carpeta del paquete que contiene el recurso.

  - `AnyAttribute*`: Un conjunto abierto de atributos que se expondrán en tiempo de ejecución como un diccionario de pares nombre-valor.

     `<AnyElement>*`: Se permite cualquier contenido estructurado entre una `<Asset>` etiqueta Begin y end. Todos los elementos se exponen como una lista de objetos XmlElement. Las extensiones VSIX pueden definir metadatos específicos del tipo estructurado en el archivo de manifiesto y enumerarlos en tiempo de ejecución.

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
 [Suministro de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
