---
title: "Cómo: revisar la ortografía en documentos mediante programación | Documentos de Microsoft"
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
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
ms.assetid: 5bbe3a8d-fc65-4f57-bd63-5bb549dbc4bd
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ce7346e25253a4c98ce8bbb8b209ccef280793d1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Cómo: Revisar la ortografía en documentos mediante programación
  Para comprobar la ortografía de un documento, use la <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> método. Este método devuelve un valor booleano que indica si el parámetro proporcionado está correctamente escrito.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Para revisar la ortografía y mostrar los resultados en un cuadro de mensaje  
  
1.  Llame a la <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> método y pasar un intervalo de texto que se va a comprobar si hay errores de ortografía. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: definir mediante programación y seleccionar rangos en documentos](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  