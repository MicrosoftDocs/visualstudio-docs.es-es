---
title: "Referencia de esquema 2.0 extensi&#243;n VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSIX"
  - "esquema de extensión"
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# Referencia de esquema 2.0 extensi&#243;n VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un archivo de manifiesto de implementación de VSIX describe el contenido de un paquete VSIX. El formato de archivo se rige por un esquema. La versión 2.0 de este esquema admite la adición de atributos y tipos personalizados.  El esquema del manifiesto es extensible. El cargador de manifiesto omite los elementos XML y atributos que no comprenda.  
  
> [!IMPORTANT]
>  Visual Studio 2015 puede cargar archivos VSIX en los formatos de Visual Studio 2010, Visual Studio 2012 o Visual Studio 2013.  
  
## Esquema del manifiesto del paquete  
 El elemento raíz del archivo XML de manifiesto es `<PackageManifest>`, con un único atributo `Version`, que es la versión del formato de manifiesto. Si se realizan cambios importantes en el formato, se cambiará el formato de versión. Este tema describe el manifiesto formato de la versión 2.0, que se especifica en el manifiesto estableciendo la `Version` en el valor de versión \= "2.0".  
  
### Elemento PackageManifest  
 Dentro de la `<PackageManifest>` elemento raíz, puede utilizar los siguientes elementos:  
  
-   `<Metadata>` \-Metadatos e información de publicidad sobre el propio paquete. Sólo un `Metadata` se admite el elemento en el manifiesto.  
  
-   `<Installation>` \-Esta sección define la manera en que puede instalar este paquete de extensión, incluidas las SKU de aplicación que pueden instalar en. Una sola `Installation` se admite el elemento en el manifiesto. Un manifiesto debe tener un `Installation` elemento o este paquete no se instala en cualquier SKU.  
  
-   `<Dependencies>` \-Una lista opcional de las dependencias de este paquete se definen aquí.  
  
-   `<Assets>` \-Esta sección contiene todos los recursos contenidos en este paquete. Sin esta sección, este paquete no revelan ningún contenido.  
  
-   `<AnyElement>*` \-El esquema del manifiesto es lo suficientemente flexible como para permitir que otros elementos. Todos los elementos secundarios no reconocidos por el cargador del manifiesto se exponen en la API del Administrador de extensiones como objetos XmlElement adicionales. Las extensiones VSIX con estos elementos secundarios, pueden definir datos adicionales en el archivo de manifiesto que puede tener acceso código que se ejecuta en Visual Studio en tiempo de ejecución. Vea <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A> y <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>.  
  
### Elemento de metadatos  
 En esta sección es los metadatos sobre el paquete, su identidad y anuncio de la información.`<Metadata>` contiene los elementos siguientes:  
  
-   `<Identity>` \-Esto define la información de identificación de este paquete e incluye los siguientes atributos:  
  
    -   `Id` : Este atributo debe ser un identificador único para el paquete elegido por su autor. Se debe calificar el nombre de la misma manera que los tipos CLR son espacios de nombres: Company.Product.Feature.Name. El `Id` atributo está limitado a 100 caracteres.  
  
    -   `Version` : Esto define la versión de este paquete y su contenido. Este atributo sigue el formato de las versiones de ensamblado CLR: principal.secundaria.compilación.revisión \(1.2.40308.00\). Un paquete con un número de versión superior se considera actualizaciones del paquete y puede instalarse en la versión instalada actualmente.  
  
    -   `Language` : Este atributo es el idioma predeterminado para el paquete y corresponde a los datos de texto en este manifiesto. Este atributo sigue la convención de código de configuración regional CLR para los ensamblados de recursos, por ejemplo: en\-us, es\-es, fr\-fr. Puede especificar `neutral` para declarar una extensión independiente del idioma que se ejecutará en cualquier versión de Visual Studio. El valor predeterminado es `neutral`.  
  
    -   `Publisher` : Este atributo identifica el publicador del paquete, una empresa o un nombre individual. El `Publisher` atributo está limitado a 100 caracteres.  
  
-   `<DisplayName>` \-Este elemento especifica el nombre del paquete fácil de usar que se muestra en la UI del Administrador de extensiones. El `DisplayName` contenido está limitado a 100 caracteres.  
  
-   `<Description>` \-Este elemento opcional es una breve descripción del paquete y su contenido se muestra en el Administrador de extensiones de UI. El `Description` contenido puede contener cualquier texto que desee, pero ha limitado a 1000 caracteres.  
  
-   `<MoreInfo>` \-Este elemento opcional es una dirección URL a una página en línea que contiene una descripción completa de este paquete. Debe especificarse el protocolo HTTP.  
  
-   `<License>` \-Este elemento opcional es una ruta de acceso relativa a un archivo de licencia \(.txt, .rtf\) contenido en el paquete.  
  
-   `<ReleaseNotes>` \-Este elemento opcional es cualquier ruta de acceso relativa a un archivo de notas de la versión contenido en el paquete \(.txt, .rtf\) o bien una dirección URL a un sitio Web que muestra las notas.  
  
-   `<Icon>` \-Este elemento opcional es una ruta de acceso relativa a un archivo de imagen \(png, bmp, jpeg, ico\) contenido en el paquete. La imagen del icono debe ser 32 x 32 píxeles \(o se reducirá a ese tamaño\) y aparece en la interfaz de usuario de listview. Si no hay ningún `Icon` se especifica, la interfaz de usuario utiliza un valor predeterminado.  
  
-   `<PreviewImage>` \-Este elemento opcional es una ruta de acceso relativa a un archivo de imagen \(png, bmp, jpeg\) contenido en el paquete. La imagen de vista previa debe ser 200 por 200 píxeles y se muestra en los detalles de la interfaz de usuario. Si no hay ningún `PreviewImage` se especifica, la interfaz de usuario utiliza un valor predeterminado.  
  
-   `<Tags>` \-Este elemento opcional muestra las etiquetas de texto delimitado por punto y coma adicional que se usan para sugerencias de búsqueda. El `Tags` elemento está limitado a 100 caracteres.  
  
-   `<GettingStartedGuide>` \-Este elemento opcional es una ruta de acceso relativa a un archivo HTML o una dirección URL a un sitio Web que contiene información acerca de cómo utilizar la extensión o el contenido dentro de este paquete. Esta guía se inicia como parte de una instalación.  
  
-   `<AnyElement>*` \-El esquema del manifiesto es lo suficientemente flexible como para permitir que otros elementos. Todos los elementos secundarios que no son reconocidos por el cargador del manifiesto se exponen como una lista de objetos. Con estos elementos secundarios, las extensiones VSIX pueden definir datos adicionales en el archivo de manifiesto y enumerarlos en tiempo de ejecución.  
  
### Elemento de la instalación  
 Esta sección define la forma en que se puede instalar este paquete y las SKU de aplicación que pueden instalar en. Esta sección contiene los siguientes atributos:  
  
-   `Experimental` : Establezca este atributo en true si tiene una extensión que está instalada actualmente para todos los usuarios, pero está desarrollando una versión actualizada en el mismo equipo. Por ejemplo, si ha instalado MyExtension 1.0 para todos los usuarios, pero desea depurar MyExtension 2.0 en el mismo equipo, establezca Experimental \= "true". Este atributo está disponible en la actualización 1 de Visual Studio 2015 y posterior.  
  
-   `Scope` : Este atributo puede tomar el valor "Global" o "ProductExtension":  
  
    -   "Global" Especifica que la instalación no se limitan a un SKU específico. Por ejemplo, este valor se utiliza cuando se instala el SDK de extensión.  
  
    -   "ProductExtension" Especifica que una extensión VSIX \(versión 1.0\) tradicional ámbito individuales SKU de Visual Studio está instalada. Este es el valor predeterminado.  
  
-   `AllUsers` : Este atributo opcional especifica si este paquete se instalará para todos los usuarios. De forma predeterminada, este atributo es false, que especifica que el paquete se por usuario. \(Cuando se establece este valor en true, el usuario que instala debe elevar a nivel de privilegios administrativos para instalar VSIX resultante.  
  
-   `InstalledByMsi` : Este atributo opcional especifica si este paquete se instala mediante un archivo MSI. Paquetes instalados por MSI se instala y se administran msi \(programas y características\) y no mediante el Administrador de extensiones de Visual Studio.  De forma predeterminada, este atributo es false, que especifica que el paquete no está instalado en un archivo MSI.  
  
-   `SystemComponent` : Este atributo opcional especifica si este paquete se debe considerar un componente del sistema. Componentes del sistema no aparecen en la UI del Administrador de extensiones y no se puede actualizar. De forma predeterminada, este atributo es false, que especifica que el paquete no es un componente del sistema.  
  
-   `AnyAttribute*` : La `Installation` elemento acepta un conjunto abierto de atributos que se expondrán en tiempo de ejecución como un diccionario de pares de nombre y valor.  
  
-   `<InstallationTarget>` : Este elemento controla la ubicación donde el instalador VSIX instala el paquete. Si el valor de la `Scope` atributo es "ProductExtension" el paquete debe tener como destino una SKU que tiene instalado un archivo de manifiesto como parte de su contenido para anunciar su disponibilidad a las extensiones. El `<InstallationTarget>` elemento tiene los siguientes atributos cuando el `Scope` atributo tiene la configuración explícita o el valor predeterminado "ProductExtension":  
  
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
  
    -   `Version` : Este atributo especifica un intervalo de versiones con las versiones admitidas de mínimas y máxima de esta SKU. Un paquete puede detallar las versiones de las SKU que admite. La notación de rango de versión es \[10.0 – 11.0\], donde  
  
        -   \[– versión mínima inclusive.  
  
        -   \] – versión máxima inclusive.  
  
        -   \(\-versión mínima exclusivo.  
  
        -   \) – versión máxima exclusiva.  
  
        -   Versión única \# \- sólo la versión especificada.  
  
        > [!IMPORTANT]
        >  La versión 2.0 del esquema VSIX se introdujo en Visual Studio 2012. Para usar este esquema debe tener Visual Studio 2012 o posterior instalado en el equipo y utilice el VSIXInstaller.exe que forma parte de ese producto. Puede tener como destino versiones anteriores de Visual Studio con Visual Studio 2012 o posterior VSIXInstaller, pero solo mediante las versiones posteriores del instalador.  
  
    -   `AnyAttribute*` : La `<InstallationTarget>` elemento permite un conjunto abierto de atributos que se exponen en tiempo de ejecución como un diccionario de pares de nombre y valor.  
  
### Elemento de dependencias  
 Este elemento contiene una lista de dependencias que se declara este paquete. Si se especifican las dependencias, los paquetes \(identificados por sus `Id`\) debe haber sido instalada antes.  
  
-   `<Dependency>` elemento: este elemento secundario tiene los siguientes atributos:  
  
    -   `Id` : Este atributo debe ser un identificador único para el paquete dependiente. Este valor de identidad debe coincidir con el `<Metadata><Identity>Id` el atributo de un paquete que depende este paquete. El `Id` atributo sigue la convención de espacio de nombres: Company.Product.Feature.Name. El atributo puede contener solo caracteres alfanuméricos y está limitado a 100 caracteres.  
  
    -   `Version` : Este atributo especifica un intervalo de versiones con las versiones admitidas de mínimas y máxima de esta SKU. Un paquete puede detallar las versiones de las SKU que admite. La notación de rango de versión es \[12.0, 13.0\], donde:  
  
        -   \[– versión mínima inclusive.  
  
        -   \] – versión máxima inclusive.  
  
        -   \(\-versión mínima exclusivo.  
  
        -   \) – versión máxima exclusiva.  
  
        -   Versión única \# \- sólo la versión especificada.  
  
    -   `DisplayName` \-Este atributo es el nombre para mostrar del paquete dependiente que se utiliza en elementos de interfaz de usuario, como cuadros de diálogo y mensajes de error. El atributo es opcional, a menos que se instala el paquete dependiente de MSI.  
  
    -   `Location` : Este atributo opcional especifica la ruta de acceso relativa dentro de este VSIX a un paquete VSIX anidado o una dirección URL a la ubicación de descarga de la dependencia. Este atributo se utiliza para ayudar al usuario a buscar el paquete de requisitos previo.  
  
    -   `AnyAttribute*` : La `Dependency` elemento acepta un conjunto abierto de atributos que se expondrán en tiempo de ejecución como un diccionario de pares de nombre y valor.  
  
### Elemento de activos  
 Este elemento contiene una lista de `<Asset>` etiquetas para cada elemento de contenido o de extensiones obtenidas por este paquete.  
  
-   `<Asset>` \-Este elemento contiene los atributos y elementos siguientes:  
  
    -   `Type` : Es el tipo de extensión o contenido representado por este elemento. Cada `<Asset>` elemento debe tener un único `Type`, pero varias `<Asset>` los elementos pueden tener el mismo `Type`. Este atributo se debe representar como un nombre completo, según las convenciones de espacio de nombres. Los tipos conocidos son:  
  
        1.  Microsoft.VisualStudio.VsPackage  
  
        2.  Microsoft.VisualStudio.MefComponent  
  
        3.  Microsoft.VisualStudio.ToolboxControl  
  
        4.  Microsoft.VisualStudio.Samples  
  
        5.  Microsoft.VisualStudio.ProjectTemplate  
  
        6.  Microsoft.VisualStudio.ItemTemplate  
  
        7.  Microsoft.VisualStudio.Assembly  
  
         Puede crear sus propios tipos y asígneles los nombres únicos. En tiempo de ejecución dentro de Visual Studio, el código puede enumerar y tener acceso a estos tipos personalizados a través de la API del Administrador de extensiones.  
  
    -   Ruta: la ruta de acceso relativa al archivo o carpeta dentro del paquete que contiene el recurso.  
  
    -   `AnyAttribute*` : Un conjunto abierto de atributos que se exponen en tiempo de ejecución como un diccionario de pares de nombre y valor.  
  
         `<AnyElement>*` : Cualquier contenido estructurado se permite entre un `<Asset>` iniciales y finales de la etiqueta. Todos los elementos se exponen como una lista de objetos. Las extensiones VSIX pueden definir los metadatos específicos del tipo estructurado en el archivo de manifiesto y enumerarlos en tiempo de ejecución.  
  
### Manifiesto de ejemplo  
  
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
  
## Vea también  
 [Envío de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)