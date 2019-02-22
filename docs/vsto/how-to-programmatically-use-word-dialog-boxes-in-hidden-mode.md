---
title: Filtrar Usar cuadros de diálogo Word en modo oculto mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e7a422e9548fabefa2066fb439c01e382586cd36
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633686"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Procedimiento Usar cuadros de diálogo Word en modo oculto mediante programación
  Puede realizar operaciones complejas con una llamada al método mediante la invocación de los cuadros de diálogo integrados en Microsoft Office Word sin mostrarlos al usuario. Puede hacerlo mediante el uso de la <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> método de la <xref:Microsoft.Office.Interop.Word.Dialog> objetos sin llamar a la <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> método.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Ejemplos
 Ejemplos de código siguientes muestran cómo usar el **Configurar página** cuadro de diálogo en modo oculto para establecer las propiedades de instalación de varias páginas sin intervención del usuario. Los ejemplos utilizan un <xref:Microsoft.Office.Interop.Word.Dialog> objeto para la configuración de un tamaño de página personalizado. La configuración específica para la configuración de página, como el margen superior, margen inferior etc., está disponible como propiedades en tiempo de ejecución de la <xref:Microsoft.Office.Interop.Word.Dialog> objeto. Estas propiedades se crean dinámicamente mediante Word en tiempo de ejecución.

 En el ejemplo siguiente se muestra cómo realizar esta tarea en proyectos de Visual Basic donde **Option Strict** está desactivada y en los proyectos de Visual C# que tienen como destino el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. En estos proyectos, puede usar las características de enlace en tiempo de ejecución en los compiladores de Visual Basic y Visual C#. Para usar este ejemplo, ejecútelo desde el `ThisDocument` o `ThisAddIn` clase del proyecto.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 En el ejemplo siguiente se muestra cómo realizar esta tarea en proyectos de Visual Basic donde **Option Strict** está activado. En estos proyectos, debe usar la reflexión para tener acceso a las propiedades enlazadas en tiempo de ejecución. Para usar este ejemplo, ejecútelo desde el `ThisDocument` o `ThisAddIn` clase del proyecto.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>Vea también
- [Cómo: Usar mediante programación los cuadros de diálogo integrados en Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)
- [Enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md)
- [Reflexión (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflexión (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
