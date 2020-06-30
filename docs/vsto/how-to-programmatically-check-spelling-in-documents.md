---
title: 'Cómo: comprobar la ortografía en documentos mediante programación'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93ba9d9907135952f7408652bfb36f440d23138d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537857"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Cómo: comprobar la ortografía en documentos mediante programación
  Para comprobar la ortografía de un documento, use el <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> método. Este método devuelve un valor booleano que indica si el parámetro proporcionado está escrito correctamente.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Para revisar la ortografía y mostrar los resultados en un cuadro de mensaje

1. Llame al <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> método y pásele un intervalo de texto para comprobar si hay errores ortográficos. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` o `ThisAddIn` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]

## <a name="see-also"></a>Consulte también
- [Cómo: definir y seleccionar intervalos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
