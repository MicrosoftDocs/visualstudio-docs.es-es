---
title: Procedimiento Mediante programación ampliar intervalos en documentos
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26213477e7cec69da9171c5197371772973be5d3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60114020"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Procedimiento Mediante programación ampliar intervalos en documentos
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

1. Defina un rango de caracteres. Para obtener más información, vea [Cómo: Definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).

     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.

     [!code-vb[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#39)]

     El siguiente ejemplo de código se puede usar en un complemento de VSTO. En este ejemplo se usa el documento activo.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#39)]

2. Use el método <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> del objeto <xref:Microsoft.Office.Interop.Word.Range> para mover la posición inicial del rango.

     [!code-vb[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#40)]
     [!code-csharp[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#40)]

3. Use el método <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> del objeto <xref:Microsoft.Office.Interop.Word.Range> para mover la posición final del rango.

     [!code-vb[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#41)]
     [!code-csharp[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#41)]

## <a name="document-level-customization-code"></a>Código de personalización de nivel de documento

### <a name="to-extend-a-range-in-a-document-level-customization"></a>Para extender un rango en una personalización de nivel de documento

1. En el siguiente ejemplo se muestra el código completo de una personalización de nivel de documento. Para usar este código, ejecútelo desde la clase `ThisDocument` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#38)]

## <a name="vsto-add-in-code"></a>Código de complementos de VSTO

### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>Para extender un rango en un complemento de VSTO de nivel de aplicación

1. En el siguiente ejemplo se muestra el código completo de un complemento de VSTO. Para usar este código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#38)]

## <a name="see-also"></a>Vea también
- [Cómo: Mediante programación restablecer intervalos en documentos de Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Cómo: Mediante programación contraer intervalos o selecciones en documentos](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Cómo: Definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Cómo: Recuperar los caracteres inicial y final en los intervalos mediante programación](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Cómo: Mediante programación excluir marcas de párrafo al crear intervalos](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
