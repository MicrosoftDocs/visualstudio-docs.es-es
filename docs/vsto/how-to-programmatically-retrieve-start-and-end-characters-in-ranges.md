---
title: Obtener caracteres finales & inicio en intervalos mediante programación
description: En este ejemplo se muestra cómo se pueden recuperar las posiciones de los caracteres de inicio y fin de un intervalo.
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4739043362a0f183574959f32a6e324d03522f65
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824034"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Cómo: Recuperar mediante programación caracteres iniciales y finales en intervalos
  En este ejemplo se muestra cómo se pueden recuperar las posiciones de los caracteres de inicio y fin de un intervalo.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Recuperar los caracteres inicial y final de un intervalo en una personalización de nivel de documento

1. Obtenga los valores de las propiedades <xref:Microsoft.Office.Interop.Word.Range.Start%2A> y <xref:Microsoft.Office.Interop.Word.Range.End%2A> del objeto <xref:Microsoft.Office.Interop.Word.Range> . En el ejemplo de código siguiente se obtienen las posiciones de inicio y fin de la segunda frase del documento. Para usar este ejemplo de código, ejecútelo desde la clase `ThisDocument` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet25":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet25":::

## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Para recuperar los caracteres inicial y final de un intervalo mediante un complemento de VSTO

1. Obtenga los valores de las propiedades <xref:Microsoft.Office.Interop.Word.Range.Start%2A> y <xref:Microsoft.Office.Interop.Word.Range.End%2A> del objeto <xref:Microsoft.Office.Interop.Word.Range> . En el ejemplo de código siguiente se obtienen las posiciones de inicio y fin de la segunda frase del documento activo. Para usar este ejemplo de código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet25":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet25":::

## <a name="see-also"></a>Consulte también
- [Cómo: Definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Cómo: Ampliar rangos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Cómo: Restablecer rangos en documentos de Word mediante programación](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Cómo: Contraer rangos o selecciones en documentos mediante programación](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Cómo: Excluir marcas de párrafo mediante programación al crear intervalos](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Cómo: Contar caracteres en documentos mediante programación](../vsto/how-to-programmatically-count-characters-in-documents.md)
