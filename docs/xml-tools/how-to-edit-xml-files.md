---
title: Procedimiento Editar archivos XML
ms.date: 11/04/2016
description: Aprenda a usar el editor XML de Visual Studio para editar archivos con contenido XML o DTD.
ms.custom: SEO-VS-2020
ms.topic: how-to
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 933ce2912845b69ceb73584c0599566b0a037fef
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399987"
---
# <a name="how-to-edit-xml-files"></a>Procedimiento Edición de archivos XML

El editor XML es el nuevo editor de archivos XML. Se puede utilizar en un archivo XML independiente o en uno asociado con un proyecto de Visual Studio. El editor XML está asociado con las siguientes extensiones de archivo: *.config*, *.dtd*, *.xml*, *.xsd*, *.xdr*, *.xsl*, *.xslt* y *.vssettings*. También está asociado con otros tipos de archivos que no tengan registrado un editor específico y que incluyan contenido XML o DTD.

> [!NOTE]
> Los documentos XHTML son manejados con el Editor HTML.

Para editar un archivo XML, abra el archivo que quiera editar.

## <a name="add-a-new-xml-file-to-a-project"></a>Incorporación de un nuevo archivo XML a un proyecto

1. En el menú **Proyecto**, seleccione **Agregar nuevo elemento**.

2. Seleccione **Archivo XML** en el panel **Plantillas**.

3. Escriba el nombre de archivo en el campo **Nombre** y presione **Agregar**.

   El archivo XML se agrega al proyecto y se abre en el editor XML. El archivo contiene la declaración XML predeterminada, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="add-an-existing-xml-file-to-a-project"></a>Incorporación de archivo XML existente a un proyecto

1. En el menú **Proyecto**, seleccione **Agregar elemento existente**.

   Aparece el cuadro de diálogo **Agregar elemento existente**.

2. Seleccione un archivo XML y presione **Agregar**.

## <a name="create-a-new-xml-or-xslt-file"></a>Creación de un nuevo archivo XML o XSLT

1. En el menú **Archivo**, seleccione **Nuevo**.

   Aparece el cuadro de diálogo **Nuevo archivo** .

2. Seleccione **Archivo XML** para crear un nuevo archivo XML; o bien, seleccione **Archivo XSLT** para crear una nueva hoja de estilos XSLT.

3. seleccione **Open**(Abrir).

## <a name="create-an-empty-project-for-xml-files"></a>Creación de un proyecto vacío para archivos XML

::: moniker range="vs-2017"

1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

   Aparecerá el cuadro de diálogo **Nuevo proyecto** .

2. Seleccione el lenguaje de código que desee y luego seleccione la plantilla **Proyecto vacío (.NET Framework)** .

3. Seleccione **Aceptar**.

::: moniker-end

::: moniker range=">=vs-2019"

1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

2. Escriba **Proyecto vacío** en el cuadro de búsqueda de plantillas, seleccione la plantilla **Proyecto vacío (.NET Framework)** y, después, **Siguiente**.

3. Seleccione **Crear**.

::: moniker-end

4. Agregue archivos XML al proyecto.

   El editor XML busca los esquemas que agregue a este proyecto y los utiliza para la validación e IntelliSense en cualquier archivo XML, de esquema o XSLT que edite mientras este proyecto está abierto.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)
- [Propiedades de documentos XML, ventana de propiedades](../xml-tools/xml-document-properties-properties-window.md)
- [Cómo: Creación de un esquema XML a partir de un documento XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
