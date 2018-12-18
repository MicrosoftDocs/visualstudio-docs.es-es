---
title: 'Cómo: cerrar documentos de Visio mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d800fbe0a6dda6fc7c5160d607d393afcb920cd9
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671578"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Cómo: cerrar documentos de Visio mediante programación
  Puede cerrar el documento de Microsoft Office Visio activo con el método `Microsoft.Office.Interop.Visio.Document.Close`.  
  
 Para obtener información más detallada sobre este método, vea la documentación de referencia de VBA del método [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) .  
  
## <a name="close-the-active-document"></a>Cerrar el documento activo  
  
### <a name="to-close-the-active-document"></a>Para cerrar el documento activo  
  
-   Llame al método `Microsoft.Office.Interop.Visio.Document.Close` para cerrar el documento activo.  
  
     Para usar el siguiente ejemplo de código, ejecútelo la `ThisAddIn` clase en un proyecto de complemento VSTO para Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)   
 [Cómo: crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Cómo: abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Cómo: guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Cómo: imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  