---
title: "Diseñador de manifiestos VSIX | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0d7af3ab109c922a8182a93db6852a331229ceca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="vsix-manifest-designer"></a>Diseñador de manifiestos de VSIX
Modifica un archivo de manifiesto de paquete VSIX, que establece el comportamiento de instalación de una extensión de Visual Studio.  
  
 El **el Diseñador de manifiestos VSIX** se asigna al esquema VSIX subyacente. Cada elemento en el esquema se puede establecer mediante un control correspondiente en el diseñador. Para obtener más información acerca del esquema, consulte [VSIX extensión de esquema 2.0 referencia](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 Para abrir el **el Diseñador de manifiestos VSIX**, busque un archivo source.extension.vsixmanifest **el Explorador de soluciones**y abra el archivo. Si el archivo no contiene XML válido, no se abrirá el Diseñador de manifiestos.  
  
> [!NOTE]
>  Source.Extension.vsixmanifest es la salida a extension.vsixmanifest cuando se crea el paquete.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 El **el Diseñador de manifiestos VSIX** contiene cuatro secciones que corresponden a estos elementos de nivel superior del esquema:  
  
-   Metadatos  
  
-   Instalar destinos  
  
-   Activos  
  
-   Dependencias  
  
 El área de encabezado contiene los siguientes controles.  
  
 **Nombre de producto**  
 Describe la extensión de nombre.  
  
 **Id. de producto**  
 Especifica la información de identificación único para este paquete.  
  
 **Autor**  
 Especifica el nombre del autor de la extensión.  
  
 **Versión**  
 Especifica el número de versión de la extensión.  
  
 El **metadatos** pestaña contiene los siguientes controles.  
  
 **Descripción**  
 Proporciona una descripción de la extensión, que se mostrará en **Extension Manager**.  
  
 **Idioma**  
 Especifica el idioma predeterminado para el paquete, que se corresponde con los datos de texto en el manifiesto. El `Language` atributo sigue la convención de código de configuración regional de common language runtime (CLR) para los ensamblados de recursos, por ejemplo, en-us, en, fr-fr. De forma predeterminada, el valor es neutro; Esto significa que el paquete se ejecutará en cualquier versión de idioma de Visual Studio.  
  
 **Licencia**  
 Especifica el archivo de texto que contiene la licencia de usuario, si hay alguno.  
  
 **Iconos**  
 Especifica el archivo de gráficos (.png, .bmp, .jpeg, .ico) que contiene el icono que se mostrará en **Administrador de extensiones**, si hay un icono. La imagen del icono debe ser 32 x 32 píxeles o se ajustará a dichas dimensiones. Si no se especifica ningún icono, **Extension Manager** utiliza un icono predeterminado.  
  
 **Imagen de vista previa**  
 Especifica el archivo de gráficos (.png, .bmp, .jpeg, .ico) que contiene la imagen de vista previa para mostrarse en **Administrador de extensiones**, si hay una imagen de vista previa. La imagen de vista previa debe ser 200 por 200 píxeles. Si no se especifica ninguna imagen de vista previa, **Extension Manager** usa una imagen predeterminada.  
  
 **Etiquetas**  
 Agrega las etiquetas de texto que se utilizarán para sugerencias de búsqueda.  
  
 **Notas de la versión**  
 Especifica un archivo (.txt, .rtf) que contiene notas de la versión. También utiliza la dirección URL de un sitio web que muestra las notas de la versión.  
  
 **Guía de introducción**  
 Especifica un archivo (.txt, .rtf) que contiene información sobre cómo usar la extensión o el contenido del paquete VSIX. Esta guía aparece una vez completada la instalación de la extensión. También toma la dirección URL de un sitio Web que muestra a la guía.  
  
 **Dirección URL para más información**  
 Especifica la dirección URL de un sitio Web que contiene información adicional sobre el producto.  
  
 El **destinos de instalación** pestaña contiene los siguientes controles.  
  
 **Tipo de instalación**  
 Enumera **extensión de Visual Studio** y **SDK de extensión** como tipos de instalación de destino. Las opciones varían según el tipo que desee.  
  
 **Extensión de Visual Studio**  
 Enumera la **InstallationTarget** elementos que describen cómo se puede instalar el paquete y en qué productos de Visual Studio se puede instalar esta extensión. Cada producto se identifica por separado por nombre y una versión o intervalo.  Productos se pueden agregar a la lista, modificar y eliminar. El nombre y la versión de un producto corresponden a la **identificador** y **versión** atributos del asociado **InstallationTarget** elemento.  
  
 **Intervalo de versiones** es [12.0, 14,0] y utiliza la notación siguiente:  
  
-   [-inclusivo de versión mínima  
  
-   ]-versión máxima inclusivo  
  
-   (-exclusivo de versión mínima  
  
-   )-versión máxima exclusivo  
  
-   Versión única # - solo la versión especificada  
  
 **SDK de extensión**  
 Especifica una instalación global que no es el ámbito de un producto específico y una versión. **Identificador de la plataforma de destino** es la plataforma, como "Windows", el destino. **Versión de la plataforma de destino** es la versión, por ejemplo, 8.0, la plataforma de destino. **Nombre de SDK** y **versión del SDK** son el nombre y el número de versión del SDK, respectivamente.  
  
 **Este VSIX se instala para todos los usuarios (requiere elevación en instale)** casilla de verificación  
 Si esta casilla está activada, esta extensión se instala para todos los usuarios; en caso contrario, se instala solo para el usuario actual.  
  
 **Este VSIX está instalado por Windows Installer** casilla de verificación  
 Si esta casilla está activada, esta extensión está instalada por Windows Installer (archivo .msi); en caso contrario, se instala como un paquete VSIX típico (archivo .vsix).  
  
 El **activos** pestaña contiene los siguientes controles.  
  
 **Lista de activos**  
 Enumera los elementos de recurso que se describen los elementos de extensión o contenido que este paquete superficies. Cada elemento de contenido o de extensiones se enumeran por separado por origen, el tipo y la ruta de acceso. Elementos de las extensiones y el contenido pueden agregados a la lista, modificar y eliminar. El tipo y la ruta de acceso de un elemento de extensión o contenido corresponde a la `Type` y `Path` atributos del asociado `Asset` elemento. Se conocen los tipos siguientes:  
  
-   Microsoft.VisualStudio.Package  
  
-   Microsoft.VisualStudio.MefComponent  
  
-   Microsoft.VisualStudio.ToolboxControl  
  
-   Microsoft.VisualStudio.Samples  
  
-   Microsoft.VisualStudio.ProjectTemplate  
  
-   Microsoft.VisualStudio.ItemTemplate  
  
-   Microsoft.VisualStudio.Assembly  
  
-   Microsoft.ExtensionSDK  
  
 Para agregar o editar un recurso, debe especificar el tipo de activo, si el recurso es un proyecto en la solución actual o un archivo en el sistema de archivos y el nombre del proyecto. También puede especificar el nombre de la carpeta en la que se va a incrustar.  
  
 También puede crear sus propios tipos y asignarles nombres únicos.  
  
 El **dependencias** pestaña contiene los siguientes controles.  
  
 **Nombre, el origen y el intervalo de versiones**  
 Enumera los elementos de la dependencia de este paquete, que son otros paquetes que depende de este paquete. Si se especifica un paquete de dependencia, debe instalarse antes de instalar este paquete; en caso contrario, este paquete debe instalarlo.  
  
 Paquetes de dependencia se especifican por identificador, nombre, intervalo de versiones, origen y cómo se puede resolver la dependencia. Cada paquete de dependencia se enumeran por separado por nombre, versión y origen. Paquetes de dependencia se pueden agregar a la lista, modificar y eliminar.  
  
 El identificador debe coincidir con el `ID` atributo de los metadatos de paquete de dependencia. El origen puede ser un proyecto en la solución actual, una extensión instalada actualmente o un archivo. El **forma dependencia resuelve** valor puede ser la ruta de acceso relativa de un paquete anidado o la dirección URL de la ubicación de descarga de la dependencia. El identificador, la versión y la resolución del paquete de dependencia corresponden a la `Id`, `Version`, y `Location` atributos del asociado `Dependency` elemento.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquema 2.0 de extensión VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)