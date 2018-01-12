---
title: "Cómo: imprimir documentos de Visio mediante programación | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a2ce41f14758d1f34c3e8c31d2ec013fa24c27b1
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-print-visio-documents"></a>Cómo: Imprimir documentos de Visio mediante programación
  Puede imprimir un documento de Microsoft Office Visio completo o solo una página concreta.  
  
 Para obtener detalles sobre los métodos de impresión, consulte la documentación de referencia de VBA de los métodos [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff767996.aspx) y [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff765064.aspx) .  
  
## <a name="printing-a-visio-document"></a>Impresión de un documento de Visio  
  
#### <a name="to-print-a-complete-document"></a>Para imprimir un documento completo  
  
-   Llame al método Microsoft.Office.Interop.Visio.Documents.Open del objeto Microsoft.Office.Interop.Visio.Document que se va a imprimir.  
  
     En el siguiente ejemplo de código se imprime el documento activo. Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]  
  
## <a name="printing-a-page-of-a-visio-document"></a>Impresión de una página de un documento de Visio  
  
#### <a name="to-print-a-page-of-a-document"></a>Para imprimir una página de un documento  
  
-   Llame al método Microsoft.Office.Interop.Visio.Pages.Print del objeto Microsoft.Office.Interop.Visio.Pages que se va a imprimir.  
  
     El siguiente ejemplo de código imprime la primera página del documento activo. Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Información general del modelo de objetos de Visio](../vsto/visio-object-model-overview.md)   
 [Cómo: crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Cómo: abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Cómo: cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Cómo: Guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  