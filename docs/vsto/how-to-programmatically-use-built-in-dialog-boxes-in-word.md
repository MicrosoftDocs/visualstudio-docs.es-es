---
title: "Cómo: usar mediante programación los cuadros de diálogo integrados en Word | Documentos de Microsoft"
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
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
ms.assetid: 0c7e4338-dead-4444-868b-3b0212368455
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7dd7d81837699aedd1c6c61d0cb0d9e2e9a64db4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Cómo: Usar cuadros de diálogo integrados en Word mediante programación
  Cuando se trabaja con Microsoft Office Word, hay ocasiones en que deba mostrar cuadros de diálogo proporcionados por el usuario. Aunque puede crear sus propias, puede que le interese tomar el enfoque del uso de los cuadros de diálogo integrados en Word, que se exponen en la <xref:Microsoft.Office.Interop.Word.Dialogs> colección de la <xref:Microsoft.Office.Interop.Word.Application> objeto. Esto le permite tener acceso a más de 200 de los cuadros de diálogo integrados, que se representan como enumeraciones.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="displaying-dialog-boxes"></a>Mostrar cuadros de diálogo  
 Para mostrar un cuadro de diálogo, utilice uno de los valores de la <xref:Microsoft.Office.Interop.Word.WdWordDialog> enumeración para crear un <xref:Microsoft.Office.Interop.Word.Dialog> objeto que representa el cuadro de diálogo que desea mostrar. A continuación, llame a la <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> método de la <xref:Microsoft.Office.Interop.Word.Dialog> objeto.  
  
 En el ejemplo de código siguiente se muestra cómo mostrar la **abrir archivo** cuadro de diálogo. Para usar este ejemplo, ejecútelo desde la `ThisDocument` o `ThisAddIn` clase en su proyecto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]  
  
### <a name="accessing-dialog-box-members-that-are-available-through-late-binding"></a>Obtener acceso a miembros de cuadro de diálogo que están disponibles a través de enlace más tarde  
 Algunas propiedades y métodos de cuadros de diálogo de Word están disponibles solo a través de enlace más tarde. En Visual Basic, proyectos where **Option Strict** está activado, debe usar la reflexión para tener acceso a estos miembros. Para obtener más información, consulta [Late Binding in Office Solutions](../vsto/late-binding-in-office-solutions.md).  
  
 En el ejemplo de código siguiente se muestra cómo utilizar el **nombre** propiedad de la **abrir archivo** cuadro de diálogo en Visual Basic proyectos where **Option Strict** está apagado o en Visual C# los proyectos que tienen como destino el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Para usar este ejemplo, ejecútelo desde la `ThisDocument` o `ThisAddIn` clase en su proyecto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 En el ejemplo de código siguiente se muestra cómo utilizar la reflexión para tener acceso a la **nombre** propiedad de la **abrir archivo** cuadro de diálogo en Visual Basic proyectos where **Option Strict** es en. Para usar este ejemplo, ejecútelo desde la `ThisDocument` o `ThisAddIn` clase en su proyecto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: usar mediante programación los cuadros de diálogo de Word en modo oculto](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)  (Option Strict (Instrucción))  
 [Reflexión (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflexión (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  