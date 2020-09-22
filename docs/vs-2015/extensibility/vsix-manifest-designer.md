---
title: Diseñador de manifiestos de VSIX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 450d306718906c3b76bf05982594045e7fd215f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842811"
---
# <a name="vsix-manifest-designer"></a>Diseñador de manifiestos de VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modifica un archivo de manifiesto del paquete VSIX, que establece el comportamiento de instalación de una extensión de Visual Studio.  
  
 El **Diseñador de manifiestos VSIX** asigna al esquema VSIX subyacente. Cada elemento del esquema se puede establecer utilizando un control correspondiente en el diseñador. Para obtener más información sobre el esquema, vea [referencia de esquema de extensión VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 Para abrir el **Diseñador de manifiestos VSIX**, busque un archivo source. Extension. vsixmanifest en **Explorador de soluciones**y abra el archivo. Si el archivo no contiene XML válido, el diseñador de manifiestos no se abrirá.  
  
> [!NOTE]
> Source. Extension. vsixmanifest se envía a extension. vsixmanifest cuando se compila el paquete.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 El **Diseñador de manifiestos VSIX** contiene cuatro secciones que corresponden a estos elementos de nivel superior del esquema:  
  
- Metadatos  
  
- Destinos de instalación  
  
- Recursos  
  
- Dependencias  
  
  El área de encabezado contiene los siguientes controles.  
  
  **Nombre del producto**  
  Describe el nombre de la extensión.  
  
  **Identificador de producto**  
  Especifica la información de identificación única para este paquete.  
  
  **Author**  
  Especifica el nombre del autor de la extensión.  
  
  **Versión**  
  Especifica el número de versión de la extensión.  
  
  La pestaña **metadatos** contiene los siguientes controles.  
  
  **Descripción**  
  Proporciona una descripción de texto de la extensión que se va a mostrar en el **Administrador de extensiones**.  
  
  **Lenguaje**  
  Especifica el idioma predeterminado del paquete, que corresponde a los datos de texto del manifiesto. El `Language` atributo sigue la Convención de código regional de Common Language Runtime (CLR) para los ensamblados de recursos, por ejemplo, en-US, en, fr-fr. De forma predeterminada, el valor es neutro; Esto significa que el paquete se ejecutará en cualquier versión de lenguaje de Visual Studio.  
  
  **Licencia**  
  Especifica el archivo de texto que contiene la licencia de usuario, si está presente.  
  
  **Icono**  
  Especifica el archivo de gráficos (. png,. bmp,. JPEG,. ico) que contiene el icono que se va a mostrar en el **Administrador de extensiones**, si hay un icono. La imagen del icono debe ser de 32 x 32 píxeles o se cambiará el tamaño de las mismas. Si no se especifica ningún icono, el **Administrador de extensiones** usa un icono predeterminado.  
  
  **Imagen de vista previa**  
  Especifica el archivo de gráficos (. png,. bmp,. JPEG,. ico) que contiene la imagen de vista previa que se va a mostrar en el **Administrador de extensiones**, si hay una imagen de vista previa. La imagen de vista previa debe ser 200 x 200 píxeles. Si no se especifica ninguna imagen de vista previa, el **Administrador de extensiones** utiliza una imagen predeterminada.  
  
  **Etiquetas**  
  Agrega etiquetas de texto que se usarán para las sugerencias de búsqueda.  
  
  **Notas de la versión**  
  Especifica un archivo (. txt,. rtf) que contiene notas de la versión. También utiliza la dirección URL de un sitio web que muestra las notas de la versión.  
  
  **Guía de introducción**  
  Especifica un archivo (. txt,. rtf) que contiene información sobre cómo usar la extensión o el contenido del paquete VSIX. Esta guía aparece cuando se completa la instalación de la extensión. También toma la dirección URL de un sitio web que muestra la guía.  
  
  **Dirección URL de más información**  
  Especifica la dirección URL de un sitio web que contiene información adicional sobre el producto.  
  
  La pestaña **destinos de instalación** contiene los siguientes controles.  
  
  **Tipo de instalación**  
  Enumera el **SDK** de extensiones y extensiones de **Visual Studio** como tipos de instalación de destino. Las opciones varían en función del tipo que elija.  
  
  **Extensión de Visual Studio**  
  Enumera los elementos **admitir** que describen cómo se puede instalar el paquete y en qué productos de Visual Studio se puede instalar esta extensión. Cada producto se identifica por separado por nombre y por versión o intervalo de versiones.  Los productos se pueden agregar a la lista, modificar y eliminar. El nombre y la versión de un producto corresponden a los atributos **ID** y **version** del elemento **admitir** asociado.  
  
  El **intervalo de versiones** es [12,0, 14,0] y usa la notación siguiente:  
  
- [– versión mínima inclusive  
  
- ]: versión máxima inclusiva  
  
- (-versión mínima exclusiva  
  
- ): versión máxima exclusiva  
  
- Versión única #: solo la versión especificada  
  
  **SDK de extensión**  
  Especifica una instalación global que no está en el ámbito de un producto y versión específicos. El identificador de la **plataforma de destino** es la plataforma, como "Windows", a la que se destina. La versión de la **plataforma de destino** es la versión, como 8,0, de la plataforma de destino. El **nombre del SDK** y la versión del **SDK** son el nombre y el número de versión del SDK, respectivamente.  
  
  **Esta casilla se instala para todos los usuarios (requiere elevación al instalar)**  
  Si esta casilla está activada, esta extensión se instala para todos los usuarios; de lo contrario, se instala solo para el usuario actual.  
  
  **Esta extensión VSIX se instala mediante Windows Installer** casilla  
  Si esta casilla está activada, el Windows Installer (archivo. msi) instala esta extensión; de lo contrario, se instala como un paquete VSIX típico (archivo. vsix).  
  
  La pestaña **activos** contiene los siguientes controles.  
  
  **Lista de activos**  
  Enumera los elementos de recursos que describen la extensión o los elementos de contenido que este paquete muestra. Cada extensión o elemento de contenido se muestra por separado en el origen, el tipo y la ruta de acceso. Los elementos de contenido y extensiones se pueden agregar a la lista, modificar y eliminar. El tipo y la ruta de acceso de una extensión o elemento de contenido corresponden a los `Type` `Path` atributos y del `Asset` elemento asociado. Se conocen los siguientes tipos:  
  
- Microsoft. VisualStudio. Package  
  
- Microsoft.VisualStudio.MefComponent  
  
- Microsoft. VisualStudio. ToolboxControl  
  
- Microsoft. VisualStudio. samples  
  
- Microsoft. VisualStudio. ProjectTemplate  
  
- Microsoft. VisualStudio. ItemTemplate  
  
- Microsoft. VisualStudio. Assembly  
  
- Microsoft. ExtensionSDK  
  
  Para agregar o editar un recurso, debe especificar el tipo de recurso, si el recurso es un proyecto en la solución actual o un archivo en el sistema de archivos, y el nombre del proyecto. También puede especificar el nombre de la carpeta en la que se va a insertar.  
  
  También puede crear sus propios tipos y asignarles nombres únicos.  
  
  La pestaña **dependencias** contiene los siguientes controles.  
  
  **Nombre, origen y intervalo de versiones**  
  Enumera los elementos de dependencia de este paquete, que son otros paquetes de los que depende este paquete. Si se especifica un paquete de dependencia, debe instalarse antes de instalar este paquete. de lo contrario, este paquete debe instalarlo.  
  
  Los paquetes de dependencia se especifican mediante el identificador, el nombre, el intervalo de versiones, el origen y el modo en que se va a resolver la dependencia. Cada paquete de dependencia se muestra por separado por nombre, versión y origen. Los paquetes de dependencia se pueden agregar a la lista, modificar y eliminar.  
  
  El identificador debe coincidir con el `ID` atributo de los metadatos del paquete de dependencia. El origen puede ser un proyecto de la solución actual, una extensión instalada actualmente o un archivo. El valor de configuración de la **dependencia resuelta** puede ser la ruta de acceso relativa de un paquete anidado o la dirección URL de la ubicación de descarga de la dependencia. El identificador, la versión y la resolución del paquete de dependencia se corresponden con los `Id` `Version` atributos, y `Location` del `Dependency` elemento asociado.  
  
## <a name="see-also"></a>Consulte también  
 [Referencia del esquema de extensión VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)
