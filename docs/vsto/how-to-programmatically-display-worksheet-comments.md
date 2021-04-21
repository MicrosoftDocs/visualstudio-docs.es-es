---
title: 'Cómo: Mostrar comentarios de hojas de cálculo mediante programación'
description: Obtenga información sobre cómo puede mostrar y ocultar comentarios en una hoja de cálculo de Microsoft Excel mediante programación en el nivel de documento o de aplicación.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af327a6756189c73f80f624205451274abf19264
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828675"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Cómo: Mostrar comentarios de hojas de cálculo mediante programación
  Puede mostrar y ocultar comentarios en las hojas de cálculo de Microsoft Office Excel mediante programación.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Para mostrar todos los comentarios de una hoja de cálculo en una personalización de nivel de documento

1. Establezca la propiedad <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> en **true** si desea mostrar los comentarios; en caso contrario, **false**. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet31":::

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Para mostrar todos los comentarios de una hoja de cálculo en un complemento de VSTO de nivel de aplicación

1. Establezca la propiedad <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> en **true** si desea mostrar los comentarios; en caso contrario, **false**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet21":::

## <a name="see-also"></a>Consulte también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Cómo: Agregar y eliminar comentarios de hojas de cálculo mediante programación](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
