---
title: Procedimiento Usar mediante programación los cuadros de diálogo integrados en Word
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: f8037e4d91aa7706c7ffd7b9f32778dfeac79488
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62961646"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Procedimiento Usar mediante programación los cuadros de diálogo integrados en Word
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
- [Cómo: Usar cuadros de diálogo Word en modo oculto mediante programación](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Option strict (instrucción)](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflexión (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflexión (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
