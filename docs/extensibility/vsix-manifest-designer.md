---
title: "Dise&#241;ador de manifiestos VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Sdk.VsixManifestEditor"
helpviewer_keywords: 
  - "vsixmanifest"
  - "manifiesto de VSIX"
  - "Diseñador de manifiestos"
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Dise&#241;ador de manifiestos VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Modifica un archivo de manifiesto de paquete VSIX, que establece el comportamiento de instalación de una extensión de Visual Studio.  
  
 El **Diseñador de manifiestos VSIX** se asigna al esquema subyacente de VSIX. Cada elemento del esquema se puede establecer mediante un control correspondiente en el diseñador. Para obtener más información acerca del esquema, consulte [Referencia de esquema 2.0 extensión VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 Para abrir el **Diseñador de manifiestos VSIX**, busque un archivo source.extension.vsixmanifest **el Explorador de soluciones**, y abra el archivo. Si el archivo no contiene XML válido, no se abrirá el Diseñador de manifiestos.  
  
> [!NOTE]
>  Source.Extension.vsixmanifest es la salida a extension.vsixmanifest cuando se compila el paquete.  
  
## Lista de UIElement  
 El **Diseñador de manifiestos VSIX** contiene cuatro secciones que corresponden a estos elementos de nivel superior del esquema:  
  
-   Metadatos  
  
-   Instalar destinos  
  
-   Activos  
  
-   Dependencias  
  
 El área de encabezado contiene los controles siguientes.  
  
 **Nombre de producto**  
 Describe el nombre de extensión.  
  
 **Id. de producto**  
 Especifica la información de identificación único para este paquete.  
  
 **Autor**  
 Especifica el nombre del autor de la extensión.  
  
 **Versión**  
 Especifica el número de versión de la extensión.  
  
 El **metadatos** ficha contiene los controles siguientes.  
  
 **Descripción**  
 Proporciona una descripción de la extensión, que se mostrará en **Administrador de extensiones de**.  
  
 **Lenguaje**  
 Especifica el idioma predeterminado para el paquete, que corresponde a los datos de texto en el manifiesto. El `Language` atributo sigue la convención de código regional de common language runtime \(CLR\) para los ensamblados de recursos, por ejemplo, en\-us, es\-es, fr\-fr. De forma predeterminada, el valor es neutro; Esto significa que el paquete se ejecutará en cualquier versión de idioma de Visual Studio.  
  
 **Licencia**  
 Especifica el archivo de texto que contiene la licencia de usuario, si hay alguno.  
  
 **Iconos**  
 Especifica el archivo de gráficos \(.png, .bmp, .jpeg, .ico\) que contiene el icono que se mostrará en **Administrador de extensiones de**, si hay un icono. La imagen del icono debe ser 32 x 32 píxeles o, se ajustará a dichas dimensiones. Si no se especifica ningún icono, **Administrador de extensiones de** utiliza un icono predeterminado.  
  
 **Imagen de vista previa**  
 Especifica el archivo de gráficos \(.png, .bmp, .jpeg, .ico\) que contiene la imagen de vista previa se muestre en **Administrador de extensiones de**, si hay una imagen de vista previa. La imagen de vista previa debe ser 200 por 200 píxeles. Si no se especifica ninguna imagen de vista previa, **Administrador de extensiones** usa una imagen predeterminada.  
  
 **Etiquetas**  
 Agrega etiquetas de texto que se utilizarán para sugerencias de búsqueda.  
  
 **Notas de la versión**  
 Especifica un archivo \(.txt, .rtf\) que contiene las notas de la versión. También utiliza la dirección URL de un sitio web que muestra las notas de la versión.  
  
 **Guía de introducción**  
 Especifica un archivo \(.txt, .rtf\) que contiene información sobre cómo usar la extensión o el contenido del paquete VSIX. Esta guía aparece cuando se complete la instalación de la extensión. También tiene la dirección URL de un sitio Web que muestra a la guía.  
  
 **Dirección URL para más información**  
 Especifica la dirección URL de un sitio Web que contiene información adicional sobre el producto.  
  
 El **destinos de instalación** ficha contiene los controles siguientes.  
  
 **Tipo de instalación**  
 Listas de **extensión de Visual Studio** y **SDK de extensión** como tipos de instalación de destino. Las opciones varían, según el tipo que elija.  
  
 **Extensión de Visual Studio**  
 Enumera la **InstallationTarget** elementos que describen cómo se puede instalar el paquete y en qué productos de Visual Studio se puede instalar esta extensión. Nombre y una versión o intervalo identifica cada producto por separado.  Productos pueden agregados a la lista, modificar y eliminar. El nombre y la versión de un producto corresponden a la **Id** y **versión** atributos de asociado **InstallationTarget** elemento.  
  
 **Intervalo de versiones** es \[12.0, 14,0\] y utiliza la notación siguiente:  
  
-   \[– versión mínima inclusivo  
  
-   \] – versión máxima inclusiva  
  
-   \(\-exclusivo de versión mínima  
  
-   \) – versión máxima exclusiva  
  
-   Versión única \# \- sólo la versión especificada  
  
 **SDK de extensión**  
 Especifica una instalación global que no se limitan a un producto específico y una versión.**Identificador de la plataforma de destino** es la plataforma, como "Windows", que tiene como destino.**Versión de la plataforma de destino** es la versión, como 8.0, la plataforma de destino.**Nombre SDK** y **SDK versión** son el nombre y el número de versión del SDK, respectivamente.  
  
 **Este VSIX se instala para todos los usuarios \(requiere la elevación en instalar\)** casilla de verificación  
 Si esta casilla está activada, esta extensión se instala para todos los usuarios; de lo contrario, se instala solo para el usuario actual.  
  
 **Este VSIX está instalado por Windows Installer** casilla de verificación  
 Si esta casilla está activada, esta extensión está instalada por Windows Installer \(archivo .msi\); de lo contrario, se instala como un paquete VSIX típico \(archivo .vsix\).  
  
 El **activos** ficha contiene los controles siguientes.  
  
 **Lista de activos**  
 Enumera los elementos de recurso que se describen los elementos de extensión o el contenido de este paquete superficies. Cada elemento de contenido o de extensiones se enumeran por separado por origen, el tipo y la ruta de acceso. Elementos extensiones y el contenido se pueden agregados a la lista, modificar y eliminar. El tipo y la ruta de acceso de un elemento de extensión o contenido corresponde a la `Type` y `Path` atributos de asociado `Asset` elemento. Se conocen los tipos siguientes:  
  
-   Microsoft.VisualStudio.Package  
  
-   Microsoft.VisualStudio.MefComponent  
  
-   Microsoft.VisualStudio.ToolboxControl  
  
-   Microsoft.VisualStudio.Samples  
  
-   Microsoft.VisualStudio.ProjectTemplate  
  
-   Microsoft.VisualStudio.ItemTemplate  
  
-   Microsoft.VisualStudio.Assembly  
  
-   Microsoft.ExtensionSDK  
  
 Para agregar o editar un recurso, debe especificar el tipo de recurso, si el recurso es un proyecto en la solución actual o un archivo en el sistema de archivos y el nombre del proyecto. También puede especificar el nombre de la carpeta en la que se va a incrustar.  
  
 También puede crear sus propios tipos y asígneles los nombres únicos.  
  
 El **dependencias** ficha contiene los controles siguientes.  
  
 **Nombre, el origen y el intervalo de versiones**  
 Enumera los elementos de dependencia de este paquete, que son otros paquetes que depende de este paquete. Si se especifica un paquete de dependencia, debe instalarse antes de instalar este paquete; de lo contrario, este paquete debe instalarlo.  
  
 Paquetes de dependencia se especifican por identificador, nombre, intervalo de versiones, origen, y cómo la dependencia se puede resolver. Cada paquete de dependencia se enumeran por separado por nombre, versión y origen. Paquetes de dependencia se pueden agregar a la lista, modificados y eliminados.  
  
 El identificador debe coincidir con el `ID` atributo de los metadatos de paquete de dependencia. El origen puede ser un proyecto en la solución actual, una extensión instalada actualmente o un archivo. El **cómo es la dependencia se resolvió** valor puede ser la ruta de acceso relativa de un paquete anidado o la dirección URL de la ubicación de descarga de la dependencia. El identificador, la versión y la resolución del paquete de dependencia corresponden a la `Id`, `Version`, y `Location` atributos de asociado `Dependency` elemento.  
  
## Vea también  
 [Referencia de esquema 2.0 extensión VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)