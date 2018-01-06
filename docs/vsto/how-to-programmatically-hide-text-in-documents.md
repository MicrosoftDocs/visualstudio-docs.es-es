---
title: "Cómo: ocultar texto en documentos mediante programación | Documentos de Microsoft"
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
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
ms.assetid: f5ced4ec-22ca-463b-b963-d34ce631b486
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 78ed00dbb7cbba80c3993932b3554dd64d3cbcf2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Cómo: Ocultar texto en documentos mediante programación
  Puede ocultar texto en un documento si establece la propiedad <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> de <xref:Microsoft.Office.Interop.Word.Range.Font%2A> para un determinado rango de texto.  
  
 Por ejemplo, puede ocultar temporalmente el texto dentro de un <xref:Microsoft.Office.Tools.Word.Bookmark> (en una personalización de nivel de documento) o un <xref:Microsoft.Office.Interop.Word.Bookmark> (en un complemento de VSTO) antes de enviar un documento a una impresora.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Para ocultar el texto de un control Bookmark al imprimir el documento  
  
1.  Cree un procedimiento que oculte todo el texto del rango especificado.  
  
     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]  
  
2.  Cree un procedimiento que muestre todo el texto del rango especificado.  
  
     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]  
  
3.  Pase el rango de un marcador al método `HideText` , imprima el documento y luego pase el mismo rango al método `UnhideText` .  
  
     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento. Para usar este ejemplo, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]  
  
     El siguiente ejemplo de código se puede usar en un complemento de VSTO. En este ejemplo se usa el documento activo. Para usar este ejemplo, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 En este ejemplo de código se supone que el documento contiene un control <xref:Microsoft.Office.Tools.Word.Bookmark> (en una personalización de nivel de documento) o un control <xref:Microsoft.Office.Interop.Word.Bookmark> (en un complemento de VSTO) que se denomina `bookmark1`.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: imprimir documentos mediante programación](../vsto/how-to-programmatically-print-documents.md)   
 [Cómo: definir mediante programación y seleccionar rangos en documentos](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Cómo: restablecer intervalos en Word documentos mediante programación](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Cómo: actualizar mediante programación el texto de marcador](../vsto/how-to-programmatically-update-bookmark-text.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  