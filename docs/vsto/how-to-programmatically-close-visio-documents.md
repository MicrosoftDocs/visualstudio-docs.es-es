---
title: Procedimiento Cerrar documentos de Visio mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 942054ea7b09525b6214cc63013bbb0c1ce5f41d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864506"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Procedimiento Cerrar documentos de Visio mediante programación
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
 [Cómo: Crear nuevos documentos de Visio mediante programación](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Cómo: Abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Cómo: Guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Cómo: Imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)  
