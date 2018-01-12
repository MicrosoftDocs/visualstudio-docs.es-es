---
title: "Cómo: mediante programación un recuento de caracteres en documentos | Documentos de Microsoft"
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
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e1d22d8fc6f6e939ec349d185dad22bdb94d176d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Cómo: Calcular un recuento de caracteres en documentos mediante programación
  El primer carácter de un documento está en la posición de carácter 0, que representa el punto de inserción. La última posición de carácter es igual al número total de caracteres del documento. Puede determinar el número de caracteres de un documento mediante la propiedad <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> de la colección <xref:Microsoft.Office.Interop.Word.Characters> .  
  
 Se cuentan todos los caracteres en el documento, incluidos los espacios, las marcas de párrafo y otros caracteres que normalmente están ocultos. Incluso un nuevo documento en blanco devuelve un recuento de caracteres porque contiene una marca de párrafo.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Para mostrar el número de caracteres en una personalización de nivel de documento  
  
1.  Seleccione todo el documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#98)]  
  
2.  Muestre el número de caracteres del documento en un cuadro de mensaje.  
  
     [!code-vb[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#99)]  
  
### <a name="to-display-the-number-of-characters-in-an-vsto-add-in"></a>Para mostrar el número de caracteres en un complemento de VSTO  
  
1.  Seleccione todo el documento. El siguiente ejemplo selecciona el documento activo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#98)]  
  
2.  Muestre el número de caracteres del documento en un cuadro de mensaje.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#99)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: recuperar los caracteres inicial y final de los intervalos mediante programación](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Cómo: Definir y seleccionar intervalos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)  
  
  