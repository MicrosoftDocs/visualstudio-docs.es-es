---
title: 'Cómo: Abrir documentos de Visio mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio para abrir un documento de Visio mediante programación con los métodos Open o OpenEx.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5f96efd41eb91551fe3cf7c03b55a44b7a9e1bf1
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824749"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Cómo: Abrir documentos de Visio mediante programación
  Hay dos métodos para abrir documentos existentes Microsoft Office Visio: Open y OpenEx. El método OpenEx es idéntico al método Open, salvo que proporciona argumentos en los que el autor de la llamada puede especificar cómo se abre el documento.

 Para obtener detalles sobre el modelo de objetos, consulte la documentación de referencia de VBA para el método [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Documents.Open) y el método [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) .

## <a name="open-a-visio-document"></a>Abrir un documento de Visio

### <a name="to-open-a-visio-document"></a>Para abrir un documento de Visio

- Llame al método `Microsoft.Office.Interop.Visio.Documents.Open` y facilite la ruta de acceso completa del documento de Visio.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet5":::

## <a name="open-a-visio-document-with-specified-arguments"></a>Apertura de un documento de Visio con argumentos especificados

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Para abrir un documento de Visio como de solo lectura y acoplado

- Llame al método `Microsoft.Office.Interop.Visio.Documents.OpenEx`, facilite la ruta de acceso completa del documento de Visio e incluya los argumentos que desea utilizar; en este caso, Docked y Read-only.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet6":::

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo de código se necesita lo siguiente:

- Un documento de Visio denominado debe encontrarse en un directorio denominado en la carpeta Mis documentos (para Windows XP y versiones anteriores) o en la carpeta `myDrawing.vsd` `Test` *Documentos* (para Windows Vista). 

## <a name="see-also"></a>Consulte también
- [Soluciones de Visio](../vsto/visio-solutions.md)
- [Introducción al modelo de objetos de Visio](../vsto/visio-object-model-overview.md)
- [Cómo: Crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Cómo: Cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)
- [Cómo: Guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)
- [Cómo: Imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)
