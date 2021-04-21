---
title: 'Cómo: Usar cuadros de diálogo integrados en Word mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio para usar mediante programación cuadros de diálogo integrados en Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6038000dec20f9183f974ad8d187230e634d5eed
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826218"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Cómo: Usar cuadros de diálogo integrados en Word mediante programación
  Al trabajar con Microsoft Office Word, hay ocasiones en las que es necesario mostrar cuadros de diálogo para la entrada del usuario. Aunque puede crear los suyos propios, también puede usar los cuadros de diálogo integrados en Word, que se exponen en la colección <xref:Microsoft.Office.Interop.Word.Dialogs> del <xref:Microsoft.Office.Interop.Word.Application> objeto . Esto le permite tener acceso a más de 200 de los cuadros de diálogo integrados, que se representan como enumeraciones.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>Mostrar cuadros de diálogo
 Para mostrar un cuadro de diálogo, use uno de los valores de la enumeración para crear un objeto que represente el cuadro de <xref:Microsoft.Office.Interop.Word.WdWordDialog> <xref:Microsoft.Office.Interop.Word.Dialog> diálogo que desea mostrar. A continuación, llame <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> al método del objeto <xref:Microsoft.Office.Interop.Word.Dialog> .

 En el ejemplo de código siguiente se muestra cómo mostrar el **cuadro de diálogo Abrir** archivo . Para usar este ejemplo, ejecute desde la clase `ThisDocument` `ThisAddIn` o del proyecto.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet100":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet100":::

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Acceder a los miembros del cuadro de diálogo que están disponibles a través del enlace en tiempo de lectura
 Algunas propiedades y métodos de los cuadros de diálogo de Word solo están disponibles a través del enlace en tiempo de entrega. En Visual Basic proyectos en los **que option Strict** está en, debe usar la reflexión para acceder a estos miembros. Para obtener más información, vea [Enlace en tiempo de tarde en soluciones de Office.](../vsto/late-binding-in-office-solutions.md)

 En el ejemplo de código siguiente se  muestra cómo usar la propiedad **Name** del cuadro de diálogo Abrir archivo en proyectos de Visual Basic donde **Option Strict** está desactivado o en proyectos de Visual C# que tienen como destino o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Para usar este ejemplo, ejecute desde la clase `ThisDocument` `ThisAddIn` o del proyecto.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet122":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet122":::

 En el ejemplo de código siguiente se muestra cómo  usar la reflexión para tener acceso a la propiedad **Name** del cuadro de diálogo Abrir archivo en Visual Basic proyectos en los que **Option Strict** está on. Para usar este ejemplo, ejecute desde la clase `ThisDocument` `ThisAddIn` o del proyecto.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet102":::

## <a name="see-also"></a>Consulte también
- [Cómo: Usar cuadros de diálogo de Word en modo oculto mediante programación](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Introducción al modelo de objetos de Word](../vsto/word-object-model-overview.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Instrucción option strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Reflexión (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection) (Reflexión [Visual Basic])
