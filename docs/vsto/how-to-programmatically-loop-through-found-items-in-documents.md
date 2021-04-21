---
title: 'Cómo: Recorrer en bucle los elementos encontrados en documentos mediante programación'
description: Obtenga información sobre cómo puede recorrer mediante programación los elementos encontrados en un documento de Microsoft Word mediante Visual Studio.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ce3153eb4e2fd7fd44318097a6b76ef6e0346086
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827349"
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>Cómo: Recorrer en bucle los elementos encontrados en documentos mediante programación
  La clase <xref:Microsoft.Office.Interop.Word.Find> tiene una propiedad <xref:Microsoft.Office.Interop.Word.Find.Found%2A> que devuelve el valor **true** cada vez que se encuentra el elemento buscado. Puede recorrer todas las instancias que se encuentran en un objeto <xref:Microsoft.Office.Interop.Word.Range> mediante el método <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-loop-through-found-items"></a>Para recorrer los elementos encontrados

1. Declare un objeto <xref:Microsoft.Office.Interop.Word.Range> .

    El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet79":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet79":::

    El siguiente ejemplo de código se puede usar en un complemento de VSTO. En este ejemplo se usa el documento activo.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet79":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet79":::

2. Use la propiedad <xref:Microsoft.Office.Interop.Word.Find.Found%2A> en un bucle para buscar todas las repeticiones de la cadena en el documento, e incremente en 1 una variable entera cada vez que se encuentre esa cadena.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet80":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet80":::

3. Muestre el número de veces que se encontró la cadena en un cuadro de mensaje.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet81":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet81":::

   En el siguiente ejemplo se muestra el método completo.

## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento

### <a name="to-loop-through-items-in-a-document-level-customization"></a>Recorrer los elementos en una personalización de nivel de documento

1. En el siguiente ejemplo se muestra el código completo de una personalización de nivel de documento. Para usar este código, ejecútelo desde la clase `ThisDocument` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet78":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet78":::

## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO

### <a name="to-loop-through-items-in-a-vsto-add-in"></a>Para recorrer en bucle los elementos de un complemento de VSTO

1. En el siguiente ejemplo se muestra el código completo de un complemento de VSTO. Para usar este código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet78":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet78":::

## <a name="see-also"></a>Consulte también
- [Cómo: Buscar y reemplazar rext en documentos mediante programación](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Cómo: Establecer opciones de búsqueda mediante programación en Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Cómo: Definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Cómo: Restaurar selecciones mediante programación después de las búsquedas](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
