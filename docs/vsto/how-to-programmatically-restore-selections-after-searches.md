---
title: "Cómo: mediante programación restaurar selecciones después de realizar búsquedas | Documentos de Microsoft"
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
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
ms.assetid: 1e6131ad-0e5b-4189-be67-5b2ed87d193d
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 28468eaba28d36394754b96bdb13727088885ff1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Cómo: Restaurar selecciones después de realizar búsquedas mediante programación
  Si Buscar y reemplazar texto en un documento, puede restaurar la selección del usuario original una vez completada la búsqueda.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 El código en el procedimiento de ejemplo hace uso de dos <xref:Microsoft.Office.Interop.Word.Range> objetos. Uno de ellos almacena actual <xref:Microsoft.Office.Interop.Word.Selection>, y el otro configura el documento completo para utilizarlo como un intervalo de búsqueda.  
  
### <a name="to-restore-the-users-original-selection-after-a-search"></a>Para restaurar la selección del usuario original después de una búsqueda  
  
1.  Crear el <xref:Microsoft.Office.Interop.Word.Range> objetos del documento y la selección actual.  
  
     [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
     [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]  
  
2.  Realizar la búsqueda y la operación de reemplazo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
     [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]  
  
3.  Seleccione el intervalo de inicio que se va a restaurar la selección del usuario original.  
  
     [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
     [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]  
  
 En el siguiente ejemplo se muestra el método completo.  
  
## <a name="example"></a>Ejemplo  
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: buscar mediante programación y reemplazar texto en documentos](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Cómo: establecer opciones de búsqueda en Word mediante programación](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Cómo: recorrer los elementos encontrados en documentos mediante programación](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  