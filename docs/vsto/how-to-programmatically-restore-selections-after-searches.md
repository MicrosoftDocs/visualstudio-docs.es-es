---
title: Procedimiento Restaurar selecciones después de realizar búsquedas mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ae27f4e24ac367741bcdf2dfa2bae8598c6c7d99
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865614"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Procedimiento Restaurar selecciones después de realizar búsquedas mediante programación
  Si Buscar y reemplazar texto en un documento, es posible que desee restaurar la selección del usuario original una vez completada la búsqueda.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 El código del procedimiento de ejemplo hace uso de dos <xref:Microsoft.Office.Interop.Word.Range> objetos. Uno de ellos almacena actual <xref:Microsoft.Office.Interop.Word.Selection>, y el otro configura todo el documento que se usará como un intervalo de búsqueda.  
  
## <a name="to-restore-the-users-original-selection-after-a-search"></a>Para restaurar la selección del usuario original después de una búsqueda  
  
1. Crear el <xref:Microsoft.Office.Interop.Word.Range> objetos para el documento y la selección actual.  
  
    [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
    [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]  
  
2. Realizar la búsqueda y la operación de reemplazo.  
  
    [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
    [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]  
  
3. Seleccione el intervalo de inicio para restaurar la selección del usuario original.  
  
    [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
    [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]  
  
   En el siguiente ejemplo se muestra el método completo.  
  
## <a name="example"></a>Ejemplo  
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Buscar y reemplazar texto en documentos mediante programación](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Cómo: Establecer opciones de búsqueda en Word mediante programación](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Cómo: Recorrer en iteración mediante programación los elementos encontrados en documentos](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
