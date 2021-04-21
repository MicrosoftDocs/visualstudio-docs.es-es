---
title: 'Cómo: Restablecer intervalos en documentos de Word mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio cambiar el tamaño de un intervalo existente en un documento de Microsoft Word mediante programación.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], resetting ranges
- ranges, resetting in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ae3b8f92231b77d81c1ef68e0929ccd000653b14
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824151"
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>Cómo: Restablecer rangos en documentos de Word mediante programación
  Use el método <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> para cambiar el tamaño de un intervalo existente en un documento de Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-reset-an-existing-range"></a>Restablecer un rango existente

1. Establezca un intervalo inicial a partir de los siete primeros caracteres del documento.

     El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet43":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet43":::

     El siguiente ejemplo de código se puede usar en un complemento de VSTO. Este código usa el documento activo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet43":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet43":::

2. Use <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> para iniciar el intervalo en la segunda oración y terminarlo al final de la quinta frase.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet44":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet44":::

## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento

### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>Restablecer un intervalo en una personalización de nivel de documento

1. En el siguiente ejemplo se muestra el ejemplo al completo de una personalización de nivel de documento. Para usar este código, ejecútelo desde la clase `ThisDocument` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet42":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet42":::

## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO

### <a name="to-reset-an-existing-range-in-a-vsto-add-in"></a>Para restablecer un intervalo existente en un complemento de VSTO

1. En el ejemplo siguiente se muestra el ejemplo completo de un complemento de VSTO. Para usar este código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet42":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet42":::

## <a name="see-also"></a>Consulte también
- [Cómo: Ampliar rangos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Cómo: Definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Cómo: Recuperar mediante programación caracteres iniciales y finales en intervalos](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Cómo: Contraer rangos o selecciones en documentos mediante programación](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
