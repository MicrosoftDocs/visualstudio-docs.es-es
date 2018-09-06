---
title: 'Cómo: recuperar los caracteres inicial y final en los intervalos mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 1244fb2ba0a9e902d4dd853e7bef25376a205a0e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674359"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Cómo: recuperar los caracteres inicial y final en los intervalos mediante programación
  En este ejemplo se muestra cómo se pueden recuperar las posiciones de los caracteres de inicio y fin de un intervalo.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Recuperar los caracteres inicial y final de un intervalo en una personalización de nivel de documento  
  
1.  Obtenga los valores de las propiedades <xref:Microsoft.Office.Interop.Word.Range.Start%2A> y <xref:Microsoft.Office.Interop.Word.Range.End%2A> del objeto <xref:Microsoft.Office.Interop.Word.Range> . En el ejemplo de código siguiente se obtienen las posiciones de inicio y fin de la segunda frase del documento. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Para recuperar los caracteres inicial y final de un intervalo mediante el uso de un complemento de VSTO  
  
1.  Obtenga los valores de las propiedades <xref:Microsoft.Office.Interop.Word.Range.Start%2A> y <xref:Microsoft.Office.Interop.Word.Range.End%2A> del objeto <xref:Microsoft.Office.Interop.Word.Range> . En el ejemplo de código siguiente se obtienen las posiciones de inicio y fin de la segunda frase del documento activo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Cómo: ampliar intervalos en documentos de mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Cómo: restablecer intervalos en documentos de Word de mediante programación](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Cómo: contraer intervalos o selecciones en documentos de mediante programación](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Cómo: excluir marcas de párrafo al crear intervalos mediante programación](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Cómo: contar mediante programación los caracteres en documentos](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  