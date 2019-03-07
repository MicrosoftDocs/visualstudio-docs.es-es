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
ms.openlocfilehash: e7da94f8fe07620a67e2df8876cf1d3adda443c5
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525458"
---
# <a name="how-to-edit-xml-files"></a>Filtrar Editar archivos XML

El editor XML es el nuevo editor de archivos XML. Se puede utilizar en un archivo XML independiente o en uno asociado con un proyecto de Visual Studio. El editor XML está asociado con las siguientes extensiones de archivo: *.config*, *.dtd*, *.xml*, *.xsd*, *.xdr*, *.xsl*, *.xslt*, y *.vssettings*. El editor XML también está asociado con ningún otro tipo de archivo que tiene no hay registrado un editor específico y que contiene el contenido XML o DTD.

> [!NOTE]
> Los documentos XHTML son manejados con el Editor HTML.

## <a name="to-edit-an-xml-file"></a>Para editar un archivo XML

1.  Haga doble clic en el archivo que desea editar.

### <a name="to-add-a-new-xml-file-to-a-project"></a>Para agregar un nuevo archivo XML a un proyecto

1.  Desde el **proyecto** menú, seleccione **Agregar nuevo elemento**.

2.  Seleccione **archivo XML** desde el **plantillas** panel.

3.  Escriba el nombre de archivo en el **nombre** campo y presione **agregar**.

     El archivo XML se agrega al proyecto y abre en el editor XML. El archivo contiene la declaración XML predeterminada, `<?xml version="1.0" encoding="utf-8" ?>`.

## <a name="to-add-an-existing-xml-file-to-a-project"></a>Para agregar un archivo XML existente a un proyecto

1.  Desde el **proyecto** menú, seleccione **Agregar elemento existente**.

     El **Agregar elemento existente** aparece el cuadro de diálogo.

2.  Seleccione un archivo XML y presione **agregar**.

## <a name="to-create-a-new-xml-or-xslt-file"></a>Para crear un nuevo archivo XML o XSLT

1.  Desde el **archivo** menú, seleccione **New**.

     El **nuevo archivo** aparece el cuadro de diálogo.

2.  Seleccione **archivo XML** para crear un nuevo archivo XML; o bien, seleccione **archivo XSLT** para crear una nueva hoja de estilos XSLT.

3.  Haga clic en **Abrir**.

## <a name="to-create-a-project-for-xml-files"></a>Para crear un proyecto de archivos XML

1.  Desde el **archivo** menú, seleccione **New**y, a continuación, seleccione **proyecto**.

     Aparecerá el cuadro de diálogo **Nuevo proyecto** .

2.  Seleccione el lenguaje de código de su elección, seleccione **proyecto vacío**y haga clic en **Aceptar**.

3.  Agregue archivos XML al proyecto.

     El editor XML busca los esquemas que agregue a este proyecto y los utiliza para la validación e IntelliSense en cualquier XML, esquema o los archivos XSLT que edite mientras este proyecto está abierto.

## <a name="see-also"></a>Vea también

- [Editor XML](../xml-tools/xml-editor.md)
- [Propiedades del documento XML, ventana Propiedades](../xml-tools/xml-document-properties-properties-window.md)
- [Cómo: Crear un esquema XML de un documento XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)