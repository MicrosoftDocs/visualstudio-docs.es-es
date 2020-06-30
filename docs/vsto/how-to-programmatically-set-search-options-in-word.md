---
title: 'Cómo: establecer opciones de búsqueda en Word mediante programación'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 434dfc85ed6c4e03c7c610a497bd063ce1826c62
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546996"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Cómo: establecer opciones de búsqueda en Word mediante programación
  Hay dos maneras de establecer las opciones de búsqueda para las selecciones en Microsoft Office documentos de Word:

- Establecer propiedades individuales de un <xref:Microsoft.Office.Interop.Word.Find> objeto.

- Usar argumentos del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método de un <xref:Microsoft.Office.Interop.Word.Find> objeto.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>Usar las propiedades de un objeto de búsqueda
 En el código siguiente se establecen las propiedades de un <xref:Microsoft.Office.Interop.Word.Find> objeto para buscar texto dentro de la selección actual. Tenga en cuenta que los criterios de búsqueda, como la búsqueda hacia delante, el ajuste y el texto que se va a buscar, son propiedades del <xref:Microsoft.Office.Interop.Word.Find> objeto.

 La configuración de cada una de las propiedades del <xref:Microsoft.Office.Interop.Word.Find> objeto no es útil cuando se escribe código de C# porque debe especificar las mismas propiedades como parámetros en el <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método. Por lo tanto, este ejemplo solo contiene código Visual Basic.

### <a name="to-set-search-options-using-a-find-object"></a>Para establecer las opciones de búsqueda mediante un objeto de búsqueda

1. Establezca las propiedades de un <xref:Microsoft.Office.Interop.Word.Find> objeto para buscar hacia delante a través de una selección del texto **buscarme**.

     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]

## <a name="use-execute-method-arguments"></a>Usar argumentos de método Execute
 En el código siguiente se usa el <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método de un <xref:Microsoft.Office.Interop.Word.Find> objeto para buscar texto dentro de la selección actual. Tenga en cuenta que los criterios de búsqueda, como la búsqueda hacia delante, el ajuste y el texto que se va a buscar, se pasan como parámetros del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método.

### <a name="to-set-search-options-using-execute-method-arguments"></a>Para establecer las opciones de búsqueda mediante los argumentos del método Execute

1. Pase los criterios de búsqueda como parámetros del <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método para buscar hacia delante a través de una selección para **Buscar**el texto.

     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]

## <a name="see-also"></a>Consulte también
- [Cómo: buscar y reemplazar texto en documentos mediante programación](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Cómo: recorrer los elementos encontrados en documentos mediante programación](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Cómo: restaurar selecciones después de realizar búsquedas mediante programación](../vsto/how-to-programmatically-restore-selections-after-searches.md)
