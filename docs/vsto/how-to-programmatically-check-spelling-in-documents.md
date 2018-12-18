---
title: 'Cómo: revisar la ortografía en documentos mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e916b16caaaa3944fcdf522ffd320198d9972b52
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256723"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Cómo: revisar la ortografía en documentos mediante programación
  Para comprobar la ortografía de un documento, use el <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> método. Este método devuelve un valor booleano que indica si el parámetro proporcionado está correctamente escrito.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Para revisar la ortografía y mostrar los resultados en un cuadro de mensaje  
  
1.  Llame a la <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> método y pásele un intervalo de texto para comprobar los errores de ortografía. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  