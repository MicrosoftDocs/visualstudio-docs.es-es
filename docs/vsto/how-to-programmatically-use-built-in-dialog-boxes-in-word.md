---
title: 'Cómo: usar cuadros de diálogo integrados en Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f5ee28b0296037b9b5490ca691a27d613c793228
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674479"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Cómo: usar cuadros de diálogo integrados en Word
  Cuando se trabaja con Microsoft Office Word, hay veces cuando se necesitan para mostrar cuadros de diálogo de intervención del usuario. Aunque puede crear sus propios, también puede tomar el enfoque del uso de los cuadros de diálogo integrados en Word, que se exponen en el <xref:Microsoft.Office.Interop.Word.Dialogs> colección de la <xref:Microsoft.Office.Interop.Word.Application> objeto. Esto le permite tener acceso a más de 200 de los cuadros de diálogo integrados, que se representan como enumeraciones.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="display-dialog-boxes"></a>Mostrar cuadros de diálogo  
 Para mostrar un cuadro de diálogo, use uno de los valores de la <xref:Microsoft.Office.Interop.Word.WdWordDialog> enumeración para crear un <xref:Microsoft.Office.Interop.Word.Dialog> objeto que representa el cuadro de diálogo que desea mostrar. A continuación, llame a la <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> método de la <xref:Microsoft.Office.Interop.Word.Dialog> objeto.  
  
 En el ejemplo de código siguiente se muestra cómo mostrar la **abrir archivo** cuadro de diálogo. Para usar este ejemplo, ejecútelo desde el `ThisDocument` o `ThisAddIn` clase del proyecto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]  
  
### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Obtener acceso a los miembros de cuadro de diálogo que están disponibles a través de enlace en tiempo de ejecución  
 Algunas propiedades y métodos de cuadros de diálogo de Word están disponibles solo a través de enlace más tarde. En Visual Basic, los proyectos donde **Option Strict** está activado, debe usar la reflexión para tener acceso a estos miembros. Para obtener más información, consulte [enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md).  
  
 En el ejemplo de código siguiente se muestra cómo usar el **nombre** propiedad de la **abrir archivo** dónde los proyectos de cuadro de diálogo en Visual Basic **Option Strict** está apagado o en Visual C# los proyectos que tienen como destino el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Para usar este ejemplo, ejecútelo desde el `ThisDocument` o `ThisAddIn` clase del proyecto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 En el ejemplo de código siguiente se muestra cómo usar la reflexión para tener acceso a la **nombre** propiedad de la **abrir archivo** dónde los proyectos de cuadro de diálogo en Visual Basic **Option Strict** es en. Para usar este ejemplo, ejecútelo desde el `ThisDocument` o `ThisAddIn` clase del proyecto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: usar cuadros de diálogo Word en modo oculto mediante programación](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Option strict (instrucción)](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflexión (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflexión (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  