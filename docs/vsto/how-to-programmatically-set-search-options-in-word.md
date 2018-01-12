---
title: "Cómo: establecer opciones de búsqueda en Word mediante programación | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fa575f8c89e9aea125179c896c35b8ecc775965e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Cómo: Establecer opciones de búsqueda en Word mediante programación
  Hay dos maneras de establecer opciones de búsqueda para las selecciones en documentos de Microsoft Office Word:  
  
-   Establecer las propiedades individuales de un <xref:Microsoft.Office.Interop.Word.Find> objeto.  
  
-   Utilice los argumentos de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método de una <xref:Microsoft.Office.Interop.Word.Find> objeto.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="using-properties-of-a-find-object"></a>Mediante las propiedades de un objeto de búsqueda  
 El código siguiente establece las propiedades de un <xref:Microsoft.Office.Interop.Word.Find> objeto para buscar texto dentro de la selección actual. Tenga en cuenta que los criterios de búsqueda, como buscar hacia delante, ajuste y texto para buscar, son propiedades de la <xref:Microsoft.Office.Interop.Word.Find> objeto.  
  
 Configuración de cada una de las propiedades de la <xref:Microsoft.Office.Interop.Word.Find> objeto no es útil cuando se escribe código de C#, ya que debe especificar las mismas propiedades como parámetros en el <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método. Por lo tanto, este ejemplo contiene solo el código de Visual Basic.  
  
#### <a name="to-set-search-options-using-a-find-object"></a>Para establecer las opciones de búsqueda con un objeto Find  
  
1.  Establecer las propiedades de un <xref:Microsoft.Office.Interop.Word.Find> objeto para buscar hacia delante a través de una selección para el texto **buscarme**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]  
  
## <a name="using-execute-method-arguments"></a>Uso de los argumentos del método Execute  
 El siguiente código utiliza el <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método de una <xref:Microsoft.Office.Interop.Word.Find> objeto para buscar texto dentro de la selección actual. Tenga en cuenta que los criterios de búsqueda, como buscar hacia delante, ajuste y texto para buscar, se pasan como parámetros de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método.  
  
#### <a name="to-set-search-options-using-execute-method-arguments"></a>Para establecer opciones de búsqueda con argumentos del método Execute  
  
1.  Pase los criterios de búsqueda como parámetros de la <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método para buscar hacia delante a través de una selección para el texto **buscarme**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: buscar mediante programación y reemplazar texto en documentos](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Cómo: recorrer los elementos encontrados en documentos mediante programación](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Cómo: Restaurar selecciones después de realizar búsquedas mediante programación](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  