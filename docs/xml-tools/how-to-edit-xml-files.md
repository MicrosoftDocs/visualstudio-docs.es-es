---
title: 'Cómo: Editar archivos XML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd8671bf45230ec24a37d5006a2d32e5aabe8f28
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645920"
---
# <a name="how-to-edit-xml-files"></a>Cómo: editar archivos XML

El editor XML es el nuevo editor de archivos XML. Se puede utilizar en un archivo XML independiente o en uno asociado con un proyecto de Visual Studio. El editor XML está asociado con las siguientes extensiones de archivo: *. config*, *. DTD*, *. XML*, *. xsd*, *. XDR*, *. xsl*, *. XSLT*y *. vssettings*. El editor XML también está asociado a cualquier otro tipo de archivo que no tenga registrado ningún editor específico y que contenga contenido XML o DTD.

> [!NOTE]
> Los documentos XHTML son manejados con el Editor HTML.

Para editar un archivo XML, haga doble clic en el archivo que desea editar.

## <a name="add-a-new-xml-file-to-a-project"></a>Agregar un nuevo archivo XML a un proyecto

1. En el menú **proyecto** , seleccione **Agregar nuevo elemento**.

2. Seleccione **archivo XML** en el panel **plantillas** .

3. Escriba el nombre de archivo en el campo **nombre** y presione **Agregar**.

   El archivo XML se agrega al proyecto y se abre en el editor XML. El archivo contiene la declaración XML predeterminada, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="add-an-existing-xml-file-to-a-project"></a>Agregar un archivo XML existente a un proyecto

1. En el menú **proyecto** , seleccione **Agregar elemento existente**.

   Aparece el cuadro de diálogo **Agregar elemento existente** .

2. Seleccione un archivo XML y presione **Agregar**.

## <a name="create-a-new-xml-or-xslt-file"></a>Crear un nuevo archivo XML o XSLT

1. En el menú **archivo** , seleccione **nuevo**.

   Aparecerá el cuadro de diálogo **nuevo archivo** .

2. Seleccione **archivo XML** para crear un nuevo archivo XML. o bien, seleccione **archivo XSLT** para crear una nueva hoja de estilos XSLT.

3. Haga clic en **Abrir**.

## <a name="create-an-empty-project-for-xml-files"></a>Crear un proyecto vacío para archivos XML

::: moniker range="vs-2017"

1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

   Aparecerá el cuadro de diálogo **Nuevo proyecto** .

2. Seleccione el lenguaje de código que desee y, a continuación, seleccione la plantilla **proyecto vacío (.NET Framework)** .

3. Haga clic en **Aceptar**.

::: moniker-end

::: moniker range=">=vs-2019"

1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

2. Escriba **proyecto vacío** en el cuadro de búsqueda de plantillas, seleccione la plantilla **proyecto vacío (.NET Framework)** y, a continuación, haga clic en **siguiente**.

3. Haga clic en **Crear**.

::: moniker-end

4. Agregue archivos XML al proyecto.

   El editor XML busca los esquemas que agrega a este proyecto y los utiliza para la validación e IntelliSense en cualquier archivo XML, esquema o XSLT que edite mientras este proyecto está abierto.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)
- [Propiedades de documento XML, ventana Propiedades](../xml-tools/xml-document-properties-properties-window.md)
- [Cómo: crear un esquema XML a partir de un documento XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)