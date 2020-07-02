---
title: 'Cómo: usar cuadros de diálogo integrados en Word mediante programación'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2c3273b22d98be1c22cf0c8cea2cb57e277b9b48
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537623"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Cómo: usar cuadros de diálogo integrados en Word mediante programación
  Cuando se trabaja con Microsoft Office Word, hay ocasiones en las que es necesario mostrar cuadros de diálogo para los datos proporcionados por el usuario. Aunque puede crear el suyo propio, es posible que también desee tomar el enfoque de usar los cuadros de diálogo integrados en Word, que se exponen en la <xref:Microsoft.Office.Interop.Word.Dialogs> colección del <xref:Microsoft.Office.Interop.Word.Application> objeto. Esto le permite tener acceso a más de 200 de los cuadros de diálogo integrados, que se representan como enumeraciones.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>Cuadros de diálogo de presentación
 Para mostrar un cuadro de diálogo, use uno de los valores de la <xref:Microsoft.Office.Interop.Word.WdWordDialog> enumeración para crear un <xref:Microsoft.Office.Interop.Word.Dialog> objeto que represente el cuadro de diálogo que desea mostrar. A continuación, llame al <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> método del <xref:Microsoft.Office.Interop.Word.Dialog> objeto.

 En el ejemplo de código siguiente se muestra cómo mostrar el cuadro de diálogo **Abrir archivo** . Para usar este ejemplo, ejecútelo desde la `ThisDocument` clase o del `ThisAddIn` proyecto.

 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Obtener acceso a miembros del cuadro de diálogo que están disponibles a través del enlace en tiempo de ejecución
 Algunas propiedades y métodos de los cuadros de diálogo de Word solo están disponibles a través del enlace en tiempo de ejecución. En Visual Basic proyectos en los que **Option Strict** está activada, debe usar la reflexión para tener acceso a estos miembros. Para obtener más información, vea [enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md).

 En el ejemplo de código siguiente se muestra cómo usar la propiedad **nombre** del cuadro de diálogo **abrir archivo** en Visual Basic Proyectos donde **Option Strict** es OFF o en proyectos de Visual C# que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Para usar este ejemplo, ejecútelo desde la `ThisDocument` clase o del `ThisAddIn` proyecto.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 En el ejemplo de código siguiente se muestra cómo usar la reflexión para tener acceso a la propiedad **nombre** del cuadro de diálogo **abrir archivo** en Visual Basic Proyectos donde **Option Strict** está activada. Para usar este ejemplo, ejecútelo desde la `ThisDocument` clase o del `ThisAddIn` proyecto.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Vea también
- [Cómo: usar cuadros de diálogo de Word en modo oculto mediante programación](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Option Strict (instrucción)](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflexión (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection) (Reflexión [Visual Basic])
