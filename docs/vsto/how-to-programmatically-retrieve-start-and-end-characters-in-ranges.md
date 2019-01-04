---
title: Procedimiento Recuperar los caracteres inicial y final en los intervalos mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9891e54986cd829c92ab3f5a5ad3a81590cf1474
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871205"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Procedimiento Recuperar los caracteres inicial y final en los intervalos mediante programación
  En este ejemplo se muestra cómo se pueden recuperar las posiciones de los caracteres de inicio y fin de un intervalo.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Recuperar los caracteres inicial y final de un intervalo en una personalización de nivel de documento  
  
1.  Obtenga los valores de las propiedades <xref:Microsoft.Office.Interop.Word.Range.Start%2A> y <xref:Microsoft.Office.Interop.Word.Range.End%2A> del objeto <xref:Microsoft.Office.Interop.Word.Range>. En el ejemplo de código siguiente se obtienen las posiciones de inicio y fin de la segunda frase del documento. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Para recuperar los caracteres inicial y final de un intervalo mediante el uso de un complemento de VSTO  
  
1.  Obtenga los valores de las propiedades <xref:Microsoft.Office.Interop.Word.Range.Start%2A> y <xref:Microsoft.Office.Interop.Word.Range.End%2A> del objeto <xref:Microsoft.Office.Interop.Word.Range> . En el ejemplo de código siguiente se obtienen las posiciones de inicio y fin de la segunda frase del documento activo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Cómo: Mediante programación ampliar intervalos en documentos](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Cómo: Mediante programación restablecer intervalos en documentos de Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Cómo: Mediante programación contraer intervalos o selecciones en documentos](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Cómo: Mediante programación excluir marcas de párrafo al crear intervalos](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Cómo: Mediante programación contar los caracteres en documentos](../vsto/how-to-programmatically-count-characters-in-documents.md)  
