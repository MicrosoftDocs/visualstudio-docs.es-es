---
title: 'Cómo: imprimir documentos de Visio mediante programación'
description: Obtenga información acerca de cómo puede imprimir un documento de Microsoft Visio completo o imprimir solo una página específica de ese documento.
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
ms.openlocfilehash: df2cd5137f05caaf7b8437fb2d903aeecc7d3e9c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933042"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Cómo: imprimir documentos de Visio mediante programación
  Puede imprimir un documento de Microsoft Office Visio completo o solo una página concreta.

 Para obtener detalles sobre los métodos de impresión, consulte la documentación de referencia de VBA de los métodos [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Document.Print) y [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Page.Print) .

## <a name="print-a-visio-document"></a>Imprimir un documento de Visio

### <a name="to-print-a-complete-document"></a>Para imprimir un documento completo

- Llame al método `Microsoft.Office.Interop.Visio.Document.Print` del objeto `Microsoft.Office.Interop.Visio.Document` que quiere imprimir.

     En el siguiente ejemplo de código se imprime el documento activo. Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]

## <a name="print-a-page-of-a-visio-document"></a>Imprimir una página de un documento de Visio

### <a name="to-print-a-page-of-a-document"></a>Para imprimir una página de un documento

- Llame al método `Microsoft.Office.Interop.Visio.Pages.Print` del objeto `Microsoft.Office.Interop.Visio.Pages` que quiere imprimir.

     El siguiente ejemplo de código imprime la primera página del documento activo. Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Vea también
- [Soluciones de Visio](../vsto/visio-solutions.md)
- [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)
- [Cómo: crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Cómo: abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)
- [Cómo: cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)
- [Cómo: guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)
