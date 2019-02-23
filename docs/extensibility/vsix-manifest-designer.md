---
title: Diseñador de manifiestos VSIX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85b9d20dd67ff11f5bded7060440f2e768a205a9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722868"
---
# <a name="vsix-manifest-designer"></a>Diseñador de manifiestos de VSIX
Modifica un archivo de manifiesto de paquete VSIX, que establece el comportamiento de instalación para una extensión de Visual Studio.

 El **el Diseñador de manifiestos VSIX** asigna al esquema VSIX subyacente. Cada elemento en el esquema puede establecerse mediante el uso de un control correspondiente en el diseñador. Para obtener más información acerca del esquema, vea [VSIX extensión de esquema 2.0 referencia](../extensibility/vsix-extension-schema-2-0-reference.md).

 Para abrir el **el Diseñador de manifiestos VSIX**, busque un *source.extension.vsixmanifest* archivo **el Explorador de soluciones**y abra el archivo. Si el archivo no contiene XML válido, no se abrirá el Diseñador de manifiestos.

> [!NOTE]
>  El *source.extension.vsixmanifest* se enviaran resultado a archivo *extension.vsixmanifest* cuando se compila el paquete.

## <a name="uielement-list"></a>Lista de UIElement
 El **el Diseñador de manifiestos VSIX** contiene cuatro secciones que corresponden a estos elementos de nivel superior del esquema:

- Metadatos

- Destinos de instalación

- Activos

- Dependencias

  El área de encabezado contiene los siguientes controles.

  **Nombre de producto** describe el nombre de extensión.

  **Id. de producto** especifica la información de identificación único para este paquete.

  **Autor** especifica el nombre del autor de la extensión.

  **Versión** especifica el número de versión de la extensión.

  El **metadatos** pestaña contiene los siguientes controles.

  **Descripción** proporciona una descripción de la extensión, que se mostrará en **Administrador de extensiones**.

  **Lenguaje** especifica el idioma predeterminado para el paquete, que corresponde a los datos de texto en el manifiesto. El `Language` atributo sigue la convención de código de configuración regional de common language runtime (CLR) para los ensamblados de recursos, por ejemplo, en-us, en, fr-fr. De forma predeterminada, el valor es neutro, lo que significa que el paquete se ejecutará en cualquier versión de idioma de Visual Studio.

  **Licencia** especifica el archivo de texto que contiene la licencia de usuario, si hay alguno.

  **Icono** especifica el archivo de gráficos (*.png*, *.bmp*, *.jpeg*, *.ico*) que contiene el icono que se mostrará en **Administrador de extensiones**, si hay un icono. La imagen del icono debe ser 32 x 32 píxeles o se cambia el tamaño a dichas dimensiones. Si no se especifica ningún icono, **Administrador de extensiones** utiliza un icono predeterminado.

  **Imagen de vista previa** especifica el archivo de gráficos (*.png*, *.bmp*, *.jpeg*, *.ico*) que contiene la imagen de vista previa se mostrará en **Administrador de extensiones**, si hay una imagen de vista previa. La imagen de vista previa debe ser 200 x 200 píxeles. Si no se especifica ninguna imagen de vista previa, **Administrador de extensiones** usa una imagen predeterminada.

  **Etiquetas** agrega etiquetas de texto que se usará para las sugerencias de búsqueda.

  **Notas de la versión** especifica un archivo (*.txt*, *.rtf*) que contiene las notas de versión. También utiliza la dirección URL de un sitio web que muestra las notas de la versión.

  **Guía de introducción** especifica un archivo (*.txt*, *.rtf*) que contiene información sobre cómo usar la extensión o el contenido del paquete VSIX. Esta guía aparece una vez completada la instalación de la extensión. También toma la dirección URL de un sitio Web que muestra a la guía.

  **URL de información adicional** especifica la dirección URL de un sitio Web que contiene información adicional sobre el producto.

  El **destinos de instalación** pestaña contiene los siguientes controles.

  **Tipo de instalación** enumera **extensión de Visual Studio** y **SDK de extensión** como tipos de instalación de destino. Las opciones varían según el tipo que elija.

  **Extensión de Visual Studio** enumera el **InstallationTarget** elementos que describen cómo se puede instalar el paquete y en qué productos de Visual Studio se puede instalar esta extensión. Nombre y una versión o intervalo identifica cada producto por separado. Productos pueden agregados a la lista, puede modificar y eliminar. El nombre y la versión de un producto corresponden a la **Id** y **versión** atributos del asociado **InstallationTarget** elemento.

  **Intervalo de versiones** es [12.0, 14,0] y utiliza la notación siguiente:

- [-inclusivo mínimo

- ]-versión máximo inclusivo

- (-exclusivo de versión mínima

- )-exclusivo de versión máxima

- Versión única # - solo la versión especificada

  **SDK de extensión** especifica una instalación global que no se limitan a un producto específico y una versión. **Identificador de la plataforma de destino** es la plataforma, como "Windows", que tiene como destino. **Versión de la plataforma de destino** es la versión, como 8.0, la plataforma de destino. **Nombre del SDK** y **SDK versión** son el nombre y el número de versión del SDK, respectivamente.

  **Este VSIX está instalado para todos los usuarios (requiere elevación en la instalación)** si selecciona esta casilla, la extensión se instala para todos los usuarios; de lo contrario, se instala solo para el usuario actual.

  **Este VSIX está instalado por Windows Installer** si selecciona esta casilla, la extensión se instala mediante el instalador de Windows (*.msi* archivo); en caso contrario, se instala como un paquete VSIX típico (*.vsix*  archivo).

  El **activos** pestaña contiene los siguientes controles.

  **Lista de activos** se enumeran los elementos de recurso que se describen los elementos de extensión o contenido que este paquete superficies. Cada extensión o un elemento de contenido se muestra por separado por origen, el tipo y la ruta de acceso. Extensiones y el contenido de los elementos se pueden agrega a la lista, modificar y eliminar. El tipo y la ruta de acceso de un elemento de extensión o contenido corresponde a la `Type` y `Path` atributos del asociado `Asset` elemento. Se conocen los tipos siguientes:

- Microsoft.VisualStudio.Package

- Microsoft.VisualStudio.MefComponent

- Microsoft.VisualStudio.ToolboxControl

- Microsoft.VisualStudio.Samples

- Microsoft.VisualStudio.ProjectTemplate

- Microsoft.VisualStudio.ItemTemplate

- Microsoft.VisualStudio.Assembly

- Microsoft.ExtensionSDK

  Para agregar o editar un recurso, debe especificar el tipo de recurso, si el recurso es un proyecto de la solución actual o un archivo en el sistema de archivos y el nombre del proyecto. También puede especificar el nombre de la carpeta en la que se va a insertarse.

  También puede crear sus propios tipos y asígneles los nombres únicos.

  El **dependencias** pestaña contiene los siguientes controles.

  **Nombre, el origen y el intervalo de versiones** se enumeran los elementos de dependencia de este paquete, que son otros paquetes que dependa de este paquete. Si se especifica un paquete de dependencias, debe instalarse antes de instalar este paquete; en caso contrario, este paquete debe instalarlo.

  Paquetes de dependencia se especifican mediante el identificador, nombre, intervalo de versiones, origen y cómo se puede resolver la dependencia. Cada paquete de dependencias se muestra por separado por nombre, versión y origen. Paquetes de dependencia se pueden agregar a la lista, modificados y eliminados.

  El identificador debe coincidir con el `ID` atributo de los metadatos del paquete de dependencia. El origen puede ser un proyecto en la solución actual, una extensión instalada actualmente o un archivo. El **cómo es la dependencia se resolvió** valor puede ser la ruta de acceso relativa de un paquete anidado o la dirección URL de la ubicación de descarga de la dependencia. El identificador, la versión y la resolución del paquete de dependencia se corresponden con los `Id`, `Version`, y `Location` atributos del asociado `Dependency` elemento.

## <a name="see-also"></a>Vea también
- [Referencia de esquema 2.0 de extensión VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)