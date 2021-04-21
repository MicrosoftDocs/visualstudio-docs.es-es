---
title: 'Cómo: Imprimir documentos de Visio mediante programación'
description: Obtenga información sobre cómo imprimir un documento completo de Microsoft Visio o imprimir solo una página específica en ese documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 13e18b1d1e20c836be740a6b44a591be6df6e926
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827193"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Cómo: Imprimir documentos de Visio mediante programación
  Puede imprimir un documento de Microsoft Office Visio completo o solo una página concreta.

 Para obtener detalles sobre los métodos de impresión, consulte la documentación de referencia de VBA de los métodos [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Document.Print) y [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Page.Print) .

## <a name="print-a-visio-document"></a>Imprimir un documento de Visio

### <a name="to-print-a-complete-document"></a>Para imprimir un documento completo

- Llame al método `Microsoft.Office.Interop.Visio.Document.Print` del objeto `Microsoft.Office.Interop.Visio.Document` que quiere imprimir.

     En el siguiente ejemplo de código se imprime el documento activo. Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet8":::

## <a name="print-a-page-of-a-visio-document"></a>Imprimir una página de un documento de Visio

### <a name="to-print-a-page-of-a-document"></a>Para imprimir una página de un documento

- Llame al método `Microsoft.Office.Interop.Visio.Pages.Print` del objeto `Microsoft.Office.Interop.Visio.Pages` que quiere imprimir.

     El siguiente ejemplo de código imprime la primera página del documento activo. Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet9":::

## <a name="see-also"></a>Consulte también
- [Soluciones de Visio](../vsto/visio-solutions.md)
- [Introducción al modelo de objetos de Visio](../vsto/visio-object-model-overview.md)
- [Cómo: Crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Cómo: Abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)
- [Cómo: Cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)
- [Cómo: Guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)
