---
title: Procedimiento Establecer opciones de búsqueda en Word mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 6e3b66bfd7f3f5d0ef0f4893efeb81c80df5d4ae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961880"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Procedimiento Establecer opciones de búsqueda en Word mediante programación
  Hay dos maneras de establecer opciones de búsqueda para las selecciones en documentos de Microsoft Office Word:

- Establezca las propiedades individuales de un <xref:Microsoft.Office.Interop.Word.Find> objeto.

- Usar argumentos de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método de un <xref:Microsoft.Office.Interop.Word.Find> objeto.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>Usar propiedades de un objeto de búsqueda
 El código siguiente establece las propiedades de un <xref:Microsoft.Office.Interop.Word.Find> objeto para buscar texto dentro de la selección actual. Tenga en cuenta que los criterios de búsqueda, como la búsqueda hacia delante, ajuste y texto para buscar, son propiedades de la <xref:Microsoft.Office.Interop.Word.Find> objeto.

 Establecer cada una de las propiedades de la <xref:Microsoft.Office.Interop.Word.Find> objeto no es útil al escribir código C#, ya que debe especificar las mismas propiedades como parámetros en el <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método. Por lo tanto, este ejemplo contiene sólo el código de Visual Basic.

### <a name="to-set-search-options-using-a-find-object"></a>Para establecer opciones de búsqueda con un objeto de búsqueda

1. Establecer las propiedades de un <xref:Microsoft.Office.Interop.Word.Find> objeto para buscar hacia delante a través de una selección para el texto **encontrarme**.

     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]

## <a name="use-execute-method-arguments"></a>Usar argumentos del método Execute
 El siguiente código utiliza el <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método de un <xref:Microsoft.Office.Interop.Word.Find> objeto para buscar texto dentro de la selección actual. Tenga en cuenta que los criterios de búsqueda, como la búsqueda hacia delante, ajuste y texto para buscar, se pasan como parámetros de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método.

### <a name="to-set-search-options-using-execute-method-arguments"></a>Para establecer opciones de búsqueda con los argumentos del método Execute

1. Pasar los criterios de búsqueda como parámetros de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método para buscar hacia delante a través de una selección para el texto **encontrarme**.

     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]

## <a name="see-also"></a>Vea también
- [Cómo: Buscar y reemplazar texto en documentos mediante programación](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Cómo: Recorrer en iteración mediante programación los elementos encontrados en documentos](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Cómo: Restaurar selecciones después de realizar búsquedas mediante programación](../vsto/how-to-programmatically-restore-selections-after-searches.md)
