---
title: Referencia del esquema de extensión VSIX 2.0 ( VSIX Extension Schema 2.0 Reference) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78e260c62d67afc10fea25d52169c48b64c82f72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697908"
---
# <a name="vsix-extension-schema-20-reference"></a>Referencia del esquema de extensión VSIX 2.0
Un archivo de manifiesto de implementación VSIX describe el contenido de un paquete VSIX. El formato de archivo se rige por un esquema. La versión 2.0 de este esquema admite la adición de tipos y atributos personalizados.  El esquema del manifiesto es extensible. El cargador de manifiestos omite los elementos y atributos XML que no entiende.

> [!IMPORTANT]
> Visual Studio 2015 puede cargar archivos VSIX en los formatos de Visual Studio 2010, Visual Studio 2012 o Visual Studio 2013.

## <a name="package-manifest-schema"></a>Esquema de manifiesto del paquete
 El elemento raíz del archivo `<PackageManifest>`XML de manifiesto es . Tiene un único `Version`atributo, que es la versión del formato de manifiesto. Si se realizan cambios importantes en el formato, se cambia el formato de versión. En este artículo se describe la versión 2.0 del `Version` formato de manifiesto, que se especifica en el manifiesto estableciendo el atributo en el valor de Version."2.0".

### <a name="packagemanifest-element"></a>Elemento PackageManifest
 Dentro `<PackageManifest>` del elemento raíz, puede utilizar los siguientes elementos:

- `<Metadata>`- Metadatos e información publicitaria sobre el propio paquete. Solo `Metadata` se permite un elemento en el manifiesto.

- `<Installation>`- Esta sección define la forma en que se puede instalar este paquete de extensión, incluidas las STU de aplicación en las que se puede instalar. Solo se `Installation` permite un único elemento en el manifiesto. Un manifiesto debe `Installation` tener un elemento o este paquete no se instalará en ninguna SKU.

- `<Dependencies>`- Aquí se define una lista opcional de dependencias para este paquete.

- `<Assets>`- Esta sección contiene todos los activos contenidos en este paquete. Sin esta sección, este paquete no saque ningún contenido.

- `<AnyElement>*`- El esquema de manifiesto es lo suficientemente flexible como para permitir cualquier otro elemento. Los elementos secundarios no reconocidos por el cargador de manifiestos se exponen en la API de Extension Manager como objetos XmlElement adicionales. Con estos elementos secundarios, las extensiones VSIX pueden definir datos adicionales en el archivo de manifiesto al que el código que se ejecuta en Visual Studio puede tener acceso en tiempo de ejecución. See [Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Elemento metadatos
 Esta sección son los metadatos sobre el paquete, su identidad e información publicitaria. `<Metadata>`contiene los siguientes elementos:

- `<Identity>`- Define la información de identificación para este paquete e incluye los siguientes atributos:

  - `Id`- Este atributo debe ser un identificador único para el paquete elegido por su autor. El nombre debe calificarse de la misma manera que los tipos CLR tienen espacio de nombres: Company.Product.Feature.Name. El `Id` atributo está limitado a 100 caracteres.

  - `Version`- Define la versión de este paquete y su contenido. Este atributo sigue el formato de control de versiones del ensamblado CLR: Major.Minor.Build.Revision (1.2.40308.00). Un paquete con un número de versión superior se considera actualizaciones del paquete y se puede instalar sobre la versión instalada existente.

  - `Language`- Este atributo es el idioma predeterminado para el paquete y corresponde a los datos textuales de este manifiesto. Este atributo sigue la convención de código de configuración regional de CLR para ensamblados de recursos, por ejemplo: en-us, en, fr-fr. Puede especificar `neutral` que se declare una extensión independiente del lenguaje que se ejecutará en cualquier versión de Visual Studio. El valor predeterminado es `neutral`.

  - `Publisher`- Este atributo identifica al editor de este paquete, ya sea una empresa o un nombre individual. El `Publisher` atributo está limitado a 100 caracteres.

- `<DisplayName>`- Este elemento especifica el nombre de paquete fácil de usar que se muestra en la interfaz de usuario del Administrador de extensiones. El `DisplayName` contenido está limitado a 50 caracteres.

- `<Description>`- Este elemento opcional es una breve descripción del paquete y su contenido que se muestra en la interfaz de usuario de Extension Manager. El `Description` contenido puede contener cualquier texto que desee, pero está limitado a 1000 caracteres.

- `<MoreInfo>`- Este elemento opcional es una dirección URL a una página en línea que contiene una descripción completa de este paquete. El protocolo debe especificarse como http.

- `<License>`- Este elemento opcional es una ruta relativa a un archivo de licencia (.txt, .rtf) contenido en el paquete.

- `<ReleaseNotes>`- Este elemento opcional es una ruta relativa a un archivo de notas de la versión contenido en el paquete (.txt, .rtf) o bien una dirección URL a un sitio web que muestra las notas de la versión.

- `<Icon>`- Este elemento opcional es una ruta relativa a un archivo de imagen (png, bmp, jpeg, ico) contenido en el paquete. La imagen del icono debe ser de 32x32 píxeles (o se reducirá a ese tamaño) y aparece en la interfaz de usuario de vista de lista. Si `Icon` no se especifica ningún elemento, la interfaz de usuario usa un valor predeterminado.

- `<PreviewImage>`- Este elemento opcional es una ruta relativa a un archivo de imagen (png, bmp, jpeg) contenido en el paquete. La imagen de vista previa debe ser de 200 x 200 píxeles y se muestra en la interfaz de usuario de detalles. Si `PreviewImage` no se especifica ningún elemento, la interfaz de usuario usa un valor predeterminado.

- `<Tags>`- Este elemento opcional enumera etiquetas de texto delimitadas por punto y coma adicionales que se utilizan para sugerencias de búsqueda. El `Tags` elemento está limitado a 100 caracteres.

- `<GettingStartedGuide>`- Este elemento opcional es una ruta relativa a un archivo HTML o una dirección URL a un sitio web que contiene información sobre cómo utilizar la extensión o el contenido dentro de este paquete. Esta guía se inicia como parte de una instalación.

- `<AnyElement>*`- El esquema de manifiesto es lo suficientemente flexible como para permitir cualquier otro elemento. Los elementos secundarios que no reconoce el cargador de manifiestos se exponen como una lista de objetos XmlElement. Con estos elementos secundarios, las extensiones VSIX pueden definir datos adicionales en el archivo de manifiesto y enumerarlos en tiempo de ejecución.

### <a name="installation-element"></a>Elemento de instalación
 En esta sección se define la forma en que se puede instalar este paquete y las STU de aplicación en las que se puede instalar. Esta sección contiene los siguientes atributos:

- `Experimental`- Establezca este atributo en true si tiene una extensión que está instalada actualmente para todos los usuarios, pero está desarrollando una versión actualizada en el mismo equipo. Por ejemplo, si ha instalado MyExtension 1.0 para todos los usuarios, pero desea depurar MyExtension 2.0 en el mismo equipo, establezca Experimental "true". Este atributo está disponible en Visual Studio 2015 Update 1 y versiones posteriores.

- `Scope`- Este atributo puede tomar el valor "Global" o "ProductExtension":

  - "Global" especifica que la instalación no tiene el ámbito de una SKU específica. Por ejemplo, este valor se utiliza cuando se instala un SDK de extensión.

  - "ProductExtension" especifica que se instala una extensión VSIX tradicional (versión 1.0) con ámbito a SKUs de Visual Studio individuales. Este es el valor predeterminado.

- `AllUsers`- Este atributo opcional especifica si este paquete se instalará para todos los usuarios. De forma predeterminada, este atributo es false, que especifica que el paquete es por usuario. (Al establecer este valor en true, el usuario de instalación debe elevar al nivel de privilegios administrativos para instalar el VSIX resultante.

- `InstalledByMsi`- Este atributo opcional especifica si este paquete está instalado por un MSI. Los paquetes instalados por un MSI son instalados y administrados por MSI (Programas y características) y no por el Administrador de extensiones de Visual Studio.  De forma predeterminada, este atributo es false, que especifica que un MSI no instala el paquete.

- `SystemComponent`- Este atributo opcional especifica si este paquete debe considerarse un componente del sistema. Los componentes del sistema no se muestran en la interfaz de usuario de Extension Manager y no se pueden actualizar. De forma predeterminada, este atributo es false, que especifica que el paquete no es un componente del sistema.

- `AnyAttribute*`- `Installation` El elemento acepta un conjunto abierto de atributos que se expondrán en tiempo de ejecución como un diccionario de pares nombre-valor.

- `<InstallationTarget>`-Este elemento controla la ubicación donde el instalador de VSIX instala el paquete. Si el valor `Scope` del atributo es "ProductExtension", el paquete debe tener como destino una SKU, que ha instalado un archivo de manifiesto como parte de su contenido para anunciar su disponibilidad a las extensiones. El `<InstallationTarget>` elemento tiene los `Scope` siguientes atributos cuando el atributo tiene el valor explícito o predeterminado "ProductExtension":

  - `Id`- Este atributo identifica el paquete.  El atributo sigue la convención de espacio de nombres: Company.Product.Feature.Name. El `Id` atributo solo puede contener caracteres alfanuméricos y está limitado a 100 caracteres. Valores esperados:

    - Microsoft.VisualStudio.IntegratedShell

    - Microsoft.VisualStudio.Pro

    - Microsoft.VisualStudio.Premium

    - Microsoft.VisualStudio.Ultimate

    - Microsoft.VisualStudio.VWDExpress

    - Microsoft.VisualStudio.VPDExpress

    - Microsoft.VisualStudio.VSWinExpress

    - Microsoft.VisualStudio.VSLS

    - My.Shell.App

  - `Version`- Este atributo especifica un intervalo de versiones con las versiones mínimas y máximas admitidas de esta SKU. Un paquete puede detallar las versiones de las STU que admite. La notación del rango de versiones es [10.0 - 11.0], donde

    - [ - versión mínima incluida.

    - ] - versión máxima incluida.

    - ( - versión mínima exclusiva.

    - ) - versión máxima exclusiva.

    - Versión única: solo la versión especificada.

    > [!IMPORTANT]
    > La versión 2.0 del esquema VSIX se introdujo en Visual Studio 2012. Para usar este esquema, debe tener Visual Studio 2012 o posterior instalado en el equipo y usar VSIXInstaller.exe que forma parte de ese producto. Puede tener como destino versiones anteriores de Visual Studio con un VSIXInstaller de Visual Studio 2012 o posterior, pero solo mediante las versiones posteriores del instalador.

    Los números de versión de Visual Studio 2017 se pueden encontrar en los números de compilación y las fechas de lanzamiento de [Visual Studio.](../install/visual-studio-build-numbers-and-release-dates.md)

    Al expresar la versión de las versiones de Visual Studio 2017, la versión secundaria siempre debe ser **0**. Por ejemplo, Visual Studio 2017 versión 15.3.26730.0 debe expresarse como [15.0.26730.0,16.0). Esto solo es necesario para Visual Studio 2017 y números de versión posteriores.

  - `AnyAttribute*`- `<InstallationTarget>` El elemento permite un conjunto abierto de atributos que se expone en tiempo de ejecución como un diccionario de pares nombre-valor.

### <a name="dependencies-element"></a>Elemento Dependencias
 Este elemento contiene una lista de dependencias que declara este paquete. Si se especifica alguna dependencia, esos paquetes (identificados por su `Id`) deben haberse instalado antes.

- `<Dependency>`elemento: este elemento secundario tiene los siguientes atributos:

  - `Id`- Este atributo debe ser un identificador único para el paquete dependiente. Este valor de `<Metadata><Identity>Id` identidad debe coincidir con el atributo de un paquete del que depende este paquete. El `Id` atributo sigue la convención de espacio de nombres: Company.Product.Feature.Name. El atributo solo puede contener caracteres alfanuméricos y está limitado a 100 caracteres.

  - `Version`- Este atributo especifica un intervalo de versiones con las versiones mínimas y máximas admitidas de esta SKU. Un paquete puede detallar las versiones de las STU que admite. La notación del rango de versiones es [12.0, 13.0], donde:

    - [ - versión mínima incluida.

    - ] - versión máxima incluida.

    - ( - versión mínima exclusiva.

    - ) - versión máxima exclusiva.

    - Versión única: solo la versión especificada.

  - `DisplayName`- Este atributo es el nombre para mostrar del paquete dependiente, que se utiliza en elementos de interfaz de usuario como cuadros de diálogo y mensajes de error. El atributo es opcional a menos que MSI instale el paquete dependiente.

  - `Location`- Este atributo opcional especifica la ruta de acceso relativa dentro de este VSIX a un paquete VSIX anidado o una dirección URL a la ubicación de descarga de la dependencia. Este atributo se utiliza para ayudar al usuario a localizar el paquete de requisitos previos.

  - `AnyAttribute*`- `Dependency` El elemento acepta un conjunto abierto de atributos que se expondrán en tiempo de ejecución como un diccionario de pares nombre-valor.

### <a name="assets-element"></a>Elemento Activos
 Este elemento contiene `<Asset>` una lista de etiquetas para cada extensión o elemento de contenido que expone este paquete.

- `<Asset>`- Este elemento contiene los siguientes atributos y elementos:

  - `Type`- Tipo de extensión o contenido representado por este elemento. Cada `<Asset>` elemento debe `Type`tener un `<Asset>` único , `Type`pero varios elementos pueden tener el mismo . Este atributo debe representarse como un nombre completo, según las convenciones de espacio de nombres. Los tipos conocidos son:

    1. Microsoft.VisualStudio.VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft.VisualStudio.ToolboxControl

    4. Microsoft.VisualStudio.Samples

    5. Microsoft.VisualStudio.ProjectTemplate

    6. Microsoft.VisualStudio.ItemTemplate

    7. Microsoft.VisualStudio.Assembly

       Puede crear sus propios tipos y darles nombres únicos. En tiempo de ejecución dentro de Visual Studio, el código puede enumerar y tener acceso a estos tipos personalizados a través de la API de Extension Manager.

  - `Path`- la ruta relativa al archivo o carpeta dentro del paquete que contiene el recurso.

  - `TargetVersion`- el rango de versiones al que se aplica el activo dado. Se utiliza para el envío de varias versiones de activos a diferentes versiones de Visual Studio. Requiere Visual Studio 2017.3 o posterior para tener efecto.

  - `AnyAttribute*`- Un conjunto abierto de atributos que se expone en tiempo de ejecución como un diccionario de pares nombre-valor.

    `<AnyElement>*`- Se permite cualquier `<Asset>` contenido estructurado entre una etiqueta de inicio y fin. Todos los elementos se exponen como una lista de XmlElement objetos. Las extensiones VSIX pueden definir metadatos específicos de tipo estructurado en el archivo de manifiesto y enumerarlos en tiempo de ejecución.

### <a name="sample-manifest"></a>Ejemplo de manifiesto

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

## <a name="see-also"></a>Vea también

- [Enviar extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
