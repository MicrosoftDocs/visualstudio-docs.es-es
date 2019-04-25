---
title: Filtrar Editar archivos XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b25eebad9efc70e4fda45131e232983e81961625
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2019
ms.locfileid: "58415062"
---
# <a name="how-to-edit-xml-files"></a>Filtrar Edición de archivos XML

El editor XML es el nuevo editor de archivos XML. Se puede utilizar en un archivo XML independiente o en uno asociado con un proyecto de Visual Studio. El editor XML está asociado con las siguientes extensiones de archivo: *.config*, *.dtd*, *.xml*, *.xsd*, *.xdr*, *.xsl*, *.xslt*, y *.vssettings*. El editor XML también está asociado con ningún otro tipo de archivo que tiene no hay registrado un editor específico y que contiene el contenido XML o DTD.

> [!NOTE]
> Los documentos XHTML son manejados con el Editor HTML.

Para editar un archivo XML, haga doble clic en el archivo que desea editar.

## <a name="add-a-new-xml-file-to-a-project"></a>Agregar un nuevo archivo XML a un proyecto

1. Desde el **proyecto** menú, seleccione **Agregar nuevo elemento**.

2. Seleccione **archivo XML** desde el **plantillas** panel.

3. Escriba el nombre de archivo en el **nombre** campo y presione **agregar**.

   El archivo XML se agrega al proyecto y se abre en el editor XML. El archivo contiene la declaración XML predeterminada, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="add-an-existing-xml-file-to-a-project"></a>Agregar un archivo XML existente a un proyecto

1. Desde el **proyecto** menú, seleccione **Agregar elemento existente**.

   El **Agregar elemento existente** aparece el cuadro de diálogo.

2. Seleccione un archivo XML y presione **agregar**.

## <a name="create-a-new-xml-or-xslt-file"></a>Cree un nuevo archivo XML o XSLT

1. Desde el **archivo** menú, seleccione **New**.

   El **nuevo archivo** aparece el cuadro de diálogo.

2. Seleccione **archivo XML** para crear un nuevo archivo XML; o bien, seleccione **archivo XSLT** para crear una nueva hoja de estilos XSLT.

3. Haga clic en **Abrir**.

## <a name="create-an-empty-project-for-xml-files"></a>Crear un proyecto vacío para los archivos XML

::: moniker range="vs-2017"

1. Desde el **archivo** menú, seleccione **New** > **proyecto**.

   Aparecerá el cuadro de diálogo **Nuevo proyecto** .

2. Seleccione el lenguaje de código de su elección, seleccione **proyecto vacío**.

3. Haga clic en **Aceptar**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Desde el **archivo** menú, seleccione **New** > **proyecto**.

2. Escriba **proyecto vacío** en el cuadro de búsqueda de la plantilla, seleccione la **proyecto vacío (.NET Framework)** plantilla y, a continuación, haga clic en **siguiente**.

3. Haga clic en **Crear**.

::: moniker-end

4. Agregue archivos XML al proyecto.

   El editor XML busca los esquemas que agregue a este proyecto y los utiliza para la validación e IntelliSense en cualquier XML, esquema o los archivos XSLT que edite mientras este proyecto está abierto.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)
- [Propiedades del documento XML, ventana Propiedades](../xml-tools/xml-document-properties-properties-window.md)
- [Cómo: Crear un esquema XML de un documento XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)