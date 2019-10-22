---
title: Procedimiento Mediante programación restablecer intervalos en documentos de Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], resetting ranges
- ranges, resetting in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 622d807da832c4c07baf8b62c902c2b1d25cc14d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955709"
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>Procedimiento Mediante programación restablecer intervalos en documentos de Word
  Use el método <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> para cambiar el tamaño de un intervalo existente en un documento de Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-reset-an-existing-range"></a>Restablecer un rango existente

1. Establezca un intervalo inicial a partir de los siete primeros caracteres del documento.

     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.

     [!code-vb[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#43)]

     El siguiente ejemplo de código se puede usar en un complemento de VSTO. Este código usa el documento activo.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#43)]

2. Use <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> para iniciar el intervalo en la segunda oración y terminarlo al final de la quinta frase.

     [!code-vb[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#44)]
     [!code-csharp[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#44)]

## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento

### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>Restablecer un intervalo en una personalización de nivel de documento

1. En el siguiente ejemplo se muestra el ejemplo al completo de una personalización de nivel de documento. Para usar este código, ejecútelo desde la clase `ThisDocument` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#42)]

## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO

### <a name="to-reset-an-existing-range-in-a-vsto-add-in"></a>Para restablecer un rango existente en un complemento de VSTO

1. El ejemplo siguiente muestra el ejemplo completo para un complemento de VSTO. Para usar este código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#42)]

## <a name="see-also"></a>Vea también
- [Cómo: Mediante programación ampliar intervalos en documentos](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Cómo: Definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Cómo: Recuperar los caracteres inicial y final en los intervalos mediante programación](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Cómo: Mediante programación contraer intervalos o selecciones en documentos](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
