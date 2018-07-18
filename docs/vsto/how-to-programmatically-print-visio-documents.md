---
title: 'Cómo: imprimir documentos de Visio mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4caf48d0268e653b7ce6f7a5c8e7efb1e2ec39e6
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257510"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Cómo: imprimir documentos de Visio mediante programación
  Puede imprimir un documento de Microsoft Office Visio completo o solo una página concreta.  
  
 Para obtener detalles sobre los métodos de impresión, consulte la documentación de referencia de VBA de los métodos [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff767996.aspx) y [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff765064.aspx) .  
  
## <a name="print-a-visio-document"></a>Imprimir un documento de Visio  
  
### <a name="to-print-a-complete-document"></a>Para imprimir un documento completo  
  
-   Llame a la `Microsoft.Office.Interop.Visio.Document.Print` método de la `Microsoft.Office.Interop.Visio.Document` objeto que se va a imprimir.  
  
     En el siguiente ejemplo de código se imprime el documento activo. Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]  
  
## <a name="print-a-page-of-a-visio-document"></a>Imprimir una página de un documento de Visio  
  
### <a name="to-print-a-page-of-a-document"></a>Para imprimir una página de un documento  
  
-   Llame a la `Microsoft.Office.Interop.Visio.Pages.Print` método de la `Microsoft.Office.Interop.Visio.Pages` objeto que se va a imprimir.  
  
     El siguiente ejemplo de código imprime la primera página del documento activo. Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)   
 [Cómo: crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Cómo: abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Cómo: cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Cómo: guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  