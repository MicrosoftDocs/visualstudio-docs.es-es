---
title: 'Cómo: recorrer los elementos encontrados en documentos mediante programación'
description: Obtenga información sobre cómo recorrer mediante programación los elementos encontrados en un documento de Microsoft Word mediante Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- loops, through found items in documents
- documents [Office development in Visual Studio], searching
- text [Office development in Visual Studio], searching in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 634012cae7f12f5346ec83bbd2b41c1019ef066d
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525626"
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>Cómo: recorrer los elementos encontrados en documentos mediante programación
  La clase <xref:Microsoft.Office.Interop.Word.Find> tiene una propiedad <xref:Microsoft.Office.Interop.Word.Find.Found%2A> que devuelve el valor **true** cada vez que se encuentra el elemento buscado. Puede recorrer todas las instancias que se encuentran en un objeto <xref:Microsoft.Office.Interop.Word.Range> mediante el método <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-loop-through-found-items"></a>Para recorrer los elementos encontrados

1. Declare un objeto <xref:Microsoft.Office.Interop.Word.Range> .

    El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.

    [!code-vb[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#79)]
    [!code-csharp[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#79)]

    El siguiente ejemplo de código se puede usar en un complemento de VSTO. En este ejemplo se usa el documento activo.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#79)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#79)]

2. Use la propiedad <xref:Microsoft.Office.Interop.Word.Find.Found%2A> en un bucle para buscar todas las repeticiones de la cadena en el documento, e incremente en 1 una variable entera cada vez que se encuentre esa cadena.

    [!code-vb[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#80)]
    [!code-csharp[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#80)]

3. Muestre el número de veces que se encontró la cadena en un cuadro de mensaje.

    [!code-vb[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#81)]
    [!code-csharp[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#81)]

   En el siguiente ejemplo se muestra el método completo.

## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento

### <a name="to-loop-through-items-in-a-document-level-customization"></a>Recorrer los elementos en una personalización de nivel de documento

1. En el siguiente ejemplo se muestra el código completo de una personalización de nivel de documento. Para usar este código, ejecútelo desde la clase `ThisDocument` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#78)]

## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO

### <a name="to-loop-through-items-in-a-vsto-add-in"></a>Para recorrer los elementos en un complemento de VSTO

1. En el siguiente ejemplo se muestra el código completo de un complemento de VSTO. Para usar este código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#78)]

## <a name="see-also"></a>Consulte también
- [Cómo: buscar y reemplazar Rext en documentos mediante programación](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Cómo: establecer opciones de búsqueda en Word mediante programación](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Cómo: definir y seleccionar intervalos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Cómo: restaurar selecciones después de realizar búsquedas mediante programación](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
