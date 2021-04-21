---
title: 'Cómo: Establecer opciones de búsqueda mediante programación en Word'
description: Obtenga información sobre cómo puede usar Visual Studio para establecer mediante programación opciones de búsqueda para selecciones en Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 605f782bf6dc3bb56b52bdcd896d1c6419cf5f51
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825035"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Cómo: Establecer opciones de búsqueda mediante programación en Word
  Hay dos maneras de establecer opciones de búsqueda para las selecciones en Microsoft Office documentos de Word:

- Establecer propiedades individuales de un <xref:Microsoft.Office.Interop.Word.Find> objeto .

- Use argumentos del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método de un objeto <xref:Microsoft.Office.Interop.Word.Find> .

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>Uso de propiedades de un objeto Find
 El código siguiente establece las propiedades de un <xref:Microsoft.Office.Interop.Word.Find> objeto para buscar texto dentro de la selección actual. Observe que los criterios de búsqueda, como la búsqueda hacia delante, el ajuste y el texto que se van a buscar, son propiedades del <xref:Microsoft.Office.Interop.Word.Find> objeto .

 Establecer cada una de las propiedades del objeto no es útil al escribir código de C#, ya que debe especificar las mismas propiedades que los <xref:Microsoft.Office.Interop.Word.Find> parámetros en el método <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> . Por lo tanto, este ejemplo solo contiene Visual Basic código.

### <a name="to-set-search-options-using-a-find-object"></a>Para establecer opciones de búsqueda mediante un objeto Find

1. Establezca las propiedades de un objeto <xref:Microsoft.Office.Interop.Word.Find> para buscar hacia delante a través de una selección para el texto find **me**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet76":::

## <a name="use-execute-method-arguments"></a>Usar argumentos del método Execute
 El código siguiente usa el <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método de un objeto para buscar texto dentro de la selección <xref:Microsoft.Office.Interop.Word.Find> actual. Observe que los criterios de búsqueda, como la búsqueda hacia delante, el ajuste y el texto que se van a buscar, se pasan como parámetros del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método .

### <a name="to-set-search-options-using-execute-method-arguments"></a>Para establecer opciones de búsqueda mediante argumentos de método Execute

1. Pase criterios de búsqueda como parámetros del método para buscar hacia <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> delante a través de una selección para el texto find **me**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet77":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet77":::

## <a name="see-also"></a>Consulte también
- [Cómo: Buscar y reemplazar texto en documentos mediante programación](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Cómo: Recorrer en bucle los elementos encontrados en documentos mediante programación](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Cómo: Restaurar selecciones mediante programación después de las búsquedas](../vsto/how-to-programmatically-restore-selections-after-searches.md)
