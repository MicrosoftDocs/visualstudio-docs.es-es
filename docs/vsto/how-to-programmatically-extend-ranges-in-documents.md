---
title: 'Cómo: ampliar intervalos en documentos de mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 810f65cbb021845c4fa659cd785e83e8c979376d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888676"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Cómo: ampliar mediante programación a intervalos en documentos
  Después de definir un objeto <xref:Microsoft.Office.Interop.Word.Range> en un documento de Microsoft Office Word, se pueden cambiar sus puntos de inicio y final mediante los métodos <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> y <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> . Los métodos <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> y <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> usan los mismos argumentos, *Unit* y *Count*. Los métodos *Count* es el número de unidades que se mueven y el argumento *Unit* puede ser uno de los siguientes valores <xref:Microsoft.Office.Interop.Word.WdUnits> :  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>  
  
- <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
  En el ejemplo siguiente se define un rango de siete caracteres. A continuación, se mueve la posición inicial del rango siete caracteres después de la posición inicial original. Puesto que la posición final del rango también estaba situada siete caracteres después de la posición inicial, el resultado es un rango que consta de cero caracteres. Posteriormente, el código mueve la posición final siete caracteres después de la posición final actual.  
  
## <a name="to-extend-a-range"></a>Para extender un rango  
  
1.  Defina un rango de caracteres. Para obtener más información, consulte [Cómo: definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).  
  
     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#39)]  
  
     El siguiente ejemplo de código se puede usar en un complemento de VSTO. En este ejemplo se usa el documento activo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#39)]  
  
2.  Use el método <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> del objeto <xref:Microsoft.Office.Interop.Word.Range> para mover la posición inicial del rango.  
  
     [!code-vb[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#40)]
     [!code-csharp[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#40)]  
  
3.  Use el método <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> del objeto <xref:Microsoft.Office.Interop.Word.Range> para mover la posición final del rango.  
  
     [!code-vb[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#41)]
     [!code-csharp[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#41)]  
  
## <a name="document-level-customization-code"></a>Código de personalización de nivel de documento  
  
### <a name="to-extend-a-range-in-a-document-level-customization"></a>Para extender un rango en una personalización de nivel de documento  
  
1.  En el siguiente ejemplo se muestra el código completo de una personalización de nivel de documento. Para usar este código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#38)]  
  
## <a name="vsto-add-in-code"></a>Código de complementos de VSTO  
  
### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>Para extender un rango en un complemento de VSTO de nivel de aplicación  
  
1.  En el siguiente ejemplo se muestra el código completo de un complemento de VSTO. Para usar este código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#38)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: restablecer intervalos en documentos de Word de mediante programación](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Cómo: contraer intervalos o selecciones en documentos de mediante programación](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Cómo: definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Cómo: recuperar los caracteres inicial y final en los intervalos mediante programación](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Cómo: excluir marcas de párrafo al crear intervalos mediante programación](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  