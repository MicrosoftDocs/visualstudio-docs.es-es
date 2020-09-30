---
title: 'Cómo: usar cuadros de diálogo de Word en modo oculto mediante programación'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 54178ecc94026499eed42da4f40f84cfe4eb831f
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583767"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Cómo: usar cuadros de diálogo de Word en modo oculto mediante programación
  Puede realizar operaciones complejas con una llamada al método invocando los cuadros de diálogo integrados en Microsoft Office Word sin mostrarlos al usuario. Puede hacerlo mediante el <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> método del <xref:Microsoft.Office.Interop.Word.Dialog> objeto sin llamar al <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> método.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Ejemplos
 En los siguientes ejemplos de código se muestra cómo usar el cuadro de diálogo **Configurar página** en modo oculto para establecer varias propiedades de configuración de página sin intervención del usuario. En los ejemplos se usa un <xref:Microsoft.Office.Interop.Word.Dialog> objeto para configurar un tamaño de página personalizado. La configuración específica de la configuración de página, como el margen superior, el margen inferior, etc., está disponible como propiedades enlazadas en tiempo de ejecución del <xref:Microsoft.Office.Interop.Word.Dialog> objeto. Word crea estas propiedades dinámicamente en tiempo de ejecución.

 En el ejemplo siguiente se muestra cómo realizar esta tarea en Visual Basic Proyectos donde **Option Strict** es OFF y en proyectos de Visual C# que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . En estos proyectos, puede usar las características de enlace en tiempo de ejecución en los compiladores de Visual Basic y Visual C#. Para usar este ejemplo, ejecútelo desde la `ThisDocument` clase o del `ThisAddIn` proyecto.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 En el ejemplo siguiente se muestra cómo realizar esta tarea en Visual Basic Proyectos donde **Option Strict** está activada. En estos proyectos, debe usar la reflexión para tener acceso a las propiedades enlazadas en tiempo de ejecución. Para usar este ejemplo, ejecútelo desde la `ThisDocument` clase o del `ThisAddIn` proyecto.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>Vea también
- [Cómo: usar cuadros de diálogo integrados en Word mediante programación](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)
- [Enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md)
- [Reflexión (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection) (Reflexión [Visual Basic])
