---
title: 'Cómo: Usar cuadros de diálogo de Word en modo oculto mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio para usar mediante programación cuadros de diálogo de Microsoft Word en modo oculto.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 39a81ccec284541d93d3a5901211d8a46ea6b61a
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826192"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Cómo: Usar cuadros de diálogo de Word en modo oculto mediante programación
  Puede realizar operaciones complejas con una llamada de método invocando los cuadros de diálogo integrados en Microsoft Office Word sin mostrarlos al usuario. Puede hacerlo mediante el método <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> del objeto sin llamar al método <xref:Microsoft.Office.Interop.Word.Dialog> <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Ejemplos
 En los ejemplos de código  siguientes se muestra cómo usar el cuadro de diálogo Configurar página en modo oculto para establecer varias propiedades de configuración de página sin entrada del usuario. En los ejemplos se usa <xref:Microsoft.Office.Interop.Word.Dialog> un objeto para configurar un tamaño de página personalizado. La configuración específica de la configuración de la página, como el margen superior, el margen inferior, y así sucesivamente, están disponibles como propiedades enlazadas en tiempo de tarde del <xref:Microsoft.Office.Interop.Word.Dialog> objeto. Word crea dinámicamente estas propiedades en tiempo de ejecución.

 En el ejemplo siguiente se muestra cómo realizar esta tarea en Visual Basic donde **Option Strict** está desactivado y en proyectos de Visual C# que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . En estos proyectos, puede usar características de enlace en tiempo de Visual Basic compiladores de Visual C#. Para usar este ejemplo, ejecute desde la `ThisDocument` clase `ThisAddIn` o del proyecto.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet123":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet123":::

 En el ejemplo siguiente se muestra cómo realizar esta tarea en Visual Basic proyectos en los **que Option Strict** está on. En estos proyectos, debe usar la reflexión para acceder a las propiedades enlazadas en tiempo de lectura. Para usar este ejemplo, ejecute desde la `ThisDocument` clase `ThisAddIn` o del proyecto.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet104":::

## <a name="see-also"></a>Consulte también
- [Cómo: Usar cuadros de diálogo integrados en Word mediante programación](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Introducción al modelo de objetos de Word](../vsto/word-object-model-overview.md)
- [Enlace en tiempo de tarde en soluciones de Office](../vsto/late-binding-in-office-solutions.md)
- [Reflexión (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection) (Reflexión [Visual Basic])
