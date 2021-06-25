---
title: Diseñador de manifiestos VSIX | Microsoft Docs
description: Obtenga información sobre cómo el Diseñador de manifiestos VSIX modifica un archivo de manifiesto de paquete VSIX, que establece el comportamiento de instalación de una Visual Studio extensión.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: baea7be60c67f186da2372c4644366b4a1a7a202
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905194"
---
# <a name="vsix-manifest-designer"></a>Diseñador de manifiestos de VSIX
Modifica un archivo de manifiesto de paquete VSIX, que establece el comportamiento de instalación de una Visual Studio extensión.

 El **Diseñador de manifiestos VSIX** se asigna al esquema VSIX subyacente. Cada elemento del esquema se puede establecer mediante un control correspondiente en el diseñador. Para obtener más información sobre el esquema, vea Referencia del esquema de extensión [VSIX 2.0.](../extensibility/vsix-extension-schema-2-0-reference.md)

 Para abrir el **Diseñador de manifiestos VSIX,** busque un *archivo source.extension.vsixmanifest* **en Explorador de soluciones** y ábralo. Si el archivo no contiene XML válido, el diseñador de manifiestos no se abrirá.

> [!NOTE]
> El *archivo source.extension.vsixmanifest* se genera en *extension.vsixmanifest* cuando se genera el paquete.

## <a name="uielement-list"></a>Lista de UIElement
 El **Diseñador de manifiestos VSIX** contiene cuatro secciones que corresponden a estos elementos de nivel superior del esquema:

- Metadatos

- Instalar destinos

- Recursos

- Dependencias

  El área de encabezado contiene los siguientes controles.

  **Nombre del producto** Describe el nombre de la extensión.

  **Id. de producto** Especifica la información de identificación única para este paquete.

  **Autor** Especifica el nombre del autor de la extensión.

  **Versión** Especifica el número de versión de la extensión.

  La **pestaña Metadatos** contiene los controles siguientes.

  **Descripción** Proporciona una descripción de texto de la extensión que se va a mostrar en el **Administrador de extensiones.**

  **Idioma** Especifica el idioma predeterminado para el paquete, que corresponde a los datos textuales del manifiesto. El atributo sigue la convención de código de configuración regional de Common Language Runtime (CLR) para los ensamblados de recursos, por `Language` ejemplo, en-us, en, fr-fr. De forma predeterminada, el valor es neutro, lo que significa que el paquete se ejecutará en cualquier versión de idioma de Visual Studio.

  **Licencia** Especifica el archivo de texto que contiene la licencia de usuario, si hay alguno.

  **Icono** Especifica el archivo de gráficos (*.png*, *.bmp*, *.jpeg*, *.ico*) que contiene el icono que se va a mostrar en el Administrador de **extensiones,** si hay un icono. La imagen de icono debe ser de 32 x 32 píxeles o se cambia de tamaño a esas dimensiones. Si no se especifica ningún icono, **el Administrador de extensiones** usa un icono predeterminado.

  **Imagen de vista previa** Especifica el archivo de gráficos (*.png*, *.bmp*, *.jpeg*, *.ico*) que contiene la imagen de vista previa que se va a mostrar en el Administrador de extensiones **,** si hay una imagen de vista previa. La imagen de vista previa debe ser de 200 x 200 píxeles. Si no se especifica ninguna imagen de vista previa, **el Administrador de extensiones** usa una imagen predeterminada.

  **Etiquetas** Agrega etiquetas de texto que se usarán para las sugerencias de búsqueda.

  **Notas de la versión** Especifica un archivo (*.txt*, *.rtf*) que contiene notas de la versión. También utiliza la dirección URL de un sitio web que muestra las notas de la versión.

  **Tareas iniciales guía** Especifica un archivo (*.txt*, *.rtf*) que contiene información sobre cómo usar la extensión o el contenido del paquete VSIX. Esta guía aparece cuando se completa la instalación de la extensión. También toma la dirección URL de un sitio web que muestra la guía.

  **Más dirección URL de información** Especifica la dirección URL de un sitio web que contiene información adicional sobre el producto.

  La **pestaña Instalar destinos** contiene los controles siguientes.

  **Tipo de instalación** Muestra **Visual Studio extensión y** el SDK de extensión **como** tipos de instalación de destino. Las opciones difieren en función del tipo que elija.

  **Visual Studio extensión** Enumera los **elementos InstallationTarget** que describen cómo se puede instalar el paquete y en qué Visual Studio productos se puede instalar esta extensión. Cada producto se identifica por separado por nombre y por un intervalo de versiones o versiones. Los productos se pueden agregar a la lista, modificar y eliminar. El nombre y la versión de un producto corresponden a los atributos **Id** y **Version** del **elemento InstallationTarget** asociado.

  **El intervalo** de versiones es [12.0, 14.0] y usa la notación siguiente:

- [ : versión mínima inclusiva

- ] : versión máxima inclusiva

- ( : versión mínima exclusiva

- ) : versión máxima exclusiva

- Número de versión única: solo la versión especificada

  **SDK de extensión** Especifica una instalación global que no tiene como ámbito un producto y una versión específicos. **El identificador de la** plataforma de destino es la plataforma, como "Windows", a la que se va a dirigir. **Versión de la plataforma** de destino es la versión, como 8.0, de la plataforma de destino. **El nombre del** SDK y **la versión** del SDK son el nombre y el número de versión del SDK, respectivamente.

  **Este VSIX se instala para todos los usuarios (requiere elevación en la instalación)** Si selecciona esta casilla, la extensión se instala para todos los usuarios; de lo contrario, solo se instala para el usuario actual.

  **Este VSIX se instala mediante Windows Installer** Si selecciona esta casilla, la extensión se instala mediante el Windows Installer (*.msi* archivo ); de lo contrario, se instala como un paquete VSIX típico *(archivo .vsix).*

  La **pestaña Activos** contiene los controles siguientes.

  **Lista de recursos** Enumera los elementos Asset que describen la extensión o los elementos de contenido que este paquete muestra. Cada extensión o elemento de contenido se muestra por separado por origen, tipo y ruta de acceso. Las extensiones y los elementos de contenido se pueden agregar a la lista, modificarse y eliminarse. El tipo y la ruta de acceso de una extensión o elemento de contenido corresponden a los `Type` atributos y del elemento `Path` `Asset` asociado. Se conocen los siguientes tipos:

- Microsoft.VisualStudio.Package

- Microsoft.VisualStudio.MefComponent

- Microsoft.VisualStudio.ToolboxControl

- Microsoft.VisualStudio.Samples

- Microsoft.VisualStudio.ProjectTemplate

- Microsoft.VisualStudio.ItemTemplate

- Microsoft.VisualStudio.Assembly

- Microsoft.ExtensionSDK

  Para agregar o editar un recurso, debe especificar el tipo de recurso, si el recurso es un proyecto de la solución actual o un archivo en el sistema de archivos y el nombre del proyecto. También puede especificar el nombre de la carpeta en la que se va a incrustar.

  También puede crear sus propios tipos y darles nombres únicos.

  La **pestaña Dependencias** contiene los controles siguientes.

  **Nombre, origen e intervalo de versiones** Enumera los elementos Dependency de este paquete, que son otros paquetes de los que depende este paquete. Si se especifica un paquete de dependencia, debe instalarse antes de instalar este paquete. De lo contrario, este paquete debe instalarlo.

  Los paquetes de dependencia se especifican por identificador, nombre, intervalo de versiones, origen y cómo se va a resolver la dependencia. Cada paquete de dependencia se muestra por separado por nombre, versión y origen. Los paquetes de dependencia se pueden agregar a la lista, modificarse y eliminarse.

  El identificador debe coincidir con el `ID` atributo de los metadatos del paquete de dependencias. El origen puede ser un proyecto de la solución actual, una extensión instalada actualmente o un archivo. El **valor How is dependency resolved** (Cómo se resuelve la dependencia) puede ser la ruta de acceso relativa de un paquete anidado o la dirección URL de la ubicación de descarga de la dependencia. El identificador, la versión y la resolución del paquete de dependencias corresponden a los atributos `Id` , y del elemento `Version` `Location` `Dependency` asociado.

## <a name="see-also"></a>Consulta también
- [Referencia del esquema de extensión VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)
