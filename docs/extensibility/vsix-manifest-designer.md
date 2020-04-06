---
title: Diseñador de manifiestos de VSIX (VSIX Manifest Designer) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30620e0fe91d0e90995d2d2f721950f878c65fdc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697890"
---
# <a name="vsix-manifest-designer"></a>Diseñador de manifiestos de VSIX
Modifica un archivo de manifiesto de paquete VSIX, que establece el comportamiento de instalación de una extensión de Visual Studio.

 El Diseñador de **manifiestos VSIX** se asigna al esquema VSIX subyacente. Cada elemento del esquema se puede establecer mediante un control correspondiente en el diseñador. Para obtener más información sobre el esquema, vea Referencia del esquema de [extensión 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)de VSIX .

 Para abrir el Diseñador de **manifiestos VSIX**, busque un archivo *source.extension.vsixmanifest* en el **Explorador**de soluciones y abra el archivo. Si el archivo no contiene XML válido, el diseñador de manifiestos no se abrirá.

> [!NOTE]
> El archivo *source.extension.vsixmanifest* se envía a *extension.vsixmanifest* cuando se compila el paquete.

## <a name="uielement-list"></a>Lista de UIElement
 El Diseñador de **manifiestos VSIX** contiene cuatro secciones que corresponden a estos elementos de nivel superior del esquema:

- Metadatos

- Objetivos de instalación

- Recursos

- Dependencias

  El área de encabezado contiene los siguientes controles.

  **Nombre del producto** Describe el nombre de la extensión.

  **ID de producto** Especifica la información de identificación única para este paquete.

  **Autor** Especifica el nombre del autor de la extensión.

  **Versión** Especifica el número de versión de la extensión.

  La pestaña **Metadatos** contiene los siguientes controles.

  **Descripción** Proporciona una descripción de texto de la extensión, que se mostrará en **el Administrador de extensiones**.

  **Idioma** Especifica el idioma predeterminado del paquete, que corresponde a los datos textuales del manifiesto. El `Language` atributo sigue la convención de código de configuración regional de Common Language Runtime (CLR) para ensamblados de recursos, por ejemplo, en-us, en, fr-fr. De forma predeterminada, el valor es neutro, lo que significa que el paquete se ejecutará en cualquier versión de idioma de Visual Studio.

  **Licencia** Especifica el archivo de texto que contiene la licencia de usuario, si hay una.

  **Icono** Especifica el archivo de gráficos (*.png*, *.bmp*, *.jpeg*, *.ico*) que contiene el icono que se mostrará en el Administrador de **extensiones**, si hay un icono presente. La imagen del icono debe ser de 32 x 32 píxeles o se cambia el tamaño a esas dimensiones. Si no se especifica ningún icono, **Extension Manager** utiliza un icono predeterminado.

  **Vista previa de la imagen** Especifica el archivo de gráficos (*.png*, *.bmp*, *.jpeg*, *.ico*) que contiene la imagen de vista previa que se mostrará en el Administrador de **extensiones**, si hay una imagen de vista previa presente. La imagen de vista previa debe tener 200 x 200 píxeles. Si no se especifica ninguna imagen de vista previa, **Extension Manager** utiliza una imagen predeterminada.

  **Etiquetas** Añade etiquetas de texto que se utilizarán para las sugerencias de búsqueda.

  **Notas de la versión** Especifica un archivo (*.txt*, *.rtf*) que contiene notas de la versión. También utiliza la dirección URL de un sitio web que muestra las notas de la versión.

  **Guía de introducción** Especifica un archivo (*.txt*, *.rtf*) que contiene información sobre cómo utilizar la extensión o el contenido del paquete VSIX. Esta guía aparece cuando se completa la instalación de la extensión. También toma la dirección URL de un sitio web que muestra la guía.

  **Más URL de información** Especifica la dirección URL de un sitio web que contiene información adicional sobre el producto.

  La pestaña **Destinos de instalación** contiene los siguientes controles.

  **Tipo de instalación** Enumera el SDK de extensión y **extensión de** **Visual Studio** como tipos de instalación de destino. Las opciones varían en función del tipo que elija.

  **Extensión de Visual Studio** Enumera los elementos **InstallationTarget** que describen cómo se puede instalar el paquete y en qué productos de Visual Studio se puede instalar esta extensión. Cada producto se identifica por separado por nombre y una versión o rango de versiones. Los productos se pueden agregar a la lista, modificar y eliminar. El nombre y la versión de un producto corresponden a los atributos **Id** y **Version** del elemento **InstallationTarget** asociado.

  El rango de **versiones** es [12.0, 14.0] y utiliza la siguiente notación:

- [ - versión mínima incluida

- ] - versión máxima incluida

- ( - versión mínima exclusiva

- ) - versión máxima exclusiva

- Versión única - sólo la versión especificada

  **SDK de extensión** Especifica una instalación global que no tiene el ámbito de un producto y una versión específicos. **Identificador** de plataforma de destino es la plataforma, como "Windows", a la que se dirige. **La versión** de plataforma de destino es la versión, como 8.0, de la plataforma de destino. **SDK Name** y **SDK Version** son el nombre y el número de versión del SDK, respectivamente.

  **Este VSIX se instala para todos los usuarios (requiere elevación en** la instalación) Si selecciona esta casilla de verificación, la extensión se instala para todos los usuarios; de lo contrario, se instala sólo para el usuario actual.

  **Este VSIX es instalado por Windows Installer** Si selecciona esta casilla de verificación, la extensión la instala Windows Installer ( archivo *.msi);* de lo contrario, se instala como un paquete VSIX típico (archivo *.vsix).*

  La pestaña **Activos** contiene los siguientes controles.

  **Lista de activos** Enumera los elementos Asset que describen los elementos de extensión o contenido que expone este paquete. Cada extensión o elemento de contenido se enumera por separado por origen, tipo y ruta de acceso. Las extensiones y los elementos de contenido se pueden agregar a la lista, modificar y eliminar. El tipo y la ruta de acceso `Type` de `Path` una extensión `Asset` o elemento de contenido corresponde a los atributos y del elemento asociado. Se conocen los siguientes tipos:

- Microsoft.VisualStudio.Package

- Microsoft.VisualStudio.MefComponent

- Microsoft.VisualStudio.ToolboxControl

- Microsoft.VisualStudio.Samples

- Microsoft.VisualStudio.ProjectTemplate

- Microsoft.VisualStudio.ItemTemplate

- Microsoft.VisualStudio.Assembly

- Microsoft.ExtensionSDK

  Para agregar o editar un activo, debe especificar el tipo de activo, si el activo es un proyecto de la solución actual o un archivo en el sistema de archivos y el nombre del proyecto. También puede especificar el nombre de la carpeta en la que se va a incrustar.

  También puede crear sus propios tipos y darles nombres únicos.

  La pestaña **Dependencias** contiene los siguientes controles.

  **Nombre, Origen y Rango de versiones** Enumera los elementos Dependency de este paquete, que son otros paquetes de los que depende este paquete. Si se especifica un paquete de dependencia, debe instalarse antes de instalar este paquete; de lo contrario, este paquete debe instalarlo.

  Los paquetes de dependencia se especifican mediante identificador, nombre, intervalo de versiones, origen y cómo se va a resolver la dependencia. Cada paquete de dependencia se enumera por separado por nombre, versión y origen. Los paquetes de dependencia se pueden agregar a la lista, modificar y eliminar.

  El identificador debe `ID` coincidir con el atributo de los metadatos del paquete de dependencia. El origen puede ser un proyecto en la solución actual, una extensión instalada actualmente o un archivo. La configuración **Cómo se resuelve por dependencia** puede ser la ruta de acceso relativa de un paquete anidado o la dirección URL de la ubicación de descarga de la dependencia. El identificador, la versión y la resolución `Id` `Version`del `Location` paquete de `Dependency` dependencia scorresponden a los atributos , , y del elemento asociado.

## <a name="see-also"></a>Vea también
- [Referencia del esquema de extensión VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)
