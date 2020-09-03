---
title: 'Cómo: mostrar los comentarios de una hoja de cálculo mediante programación'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0fc84e2726cd7a70b8fc59b0f1ac2b3377f9c4af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543369"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Cómo: mostrar los comentarios de una hoja de cálculo mediante programación
  Puede mostrar y ocultar comentarios en las hojas de cálculo de Microsoft Office Excel mediante programación.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Para mostrar todos los comentarios de una hoja de cálculo en una personalización de nivel de documento

1. Establezca la propiedad <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> en **true** si desea mostrar los comentarios; en caso contrario, **false**. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Para mostrar todos los comentarios de una hoja de cálculo en un complemento de VSTO de nivel de aplicación

1. Establezca la propiedad <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> en **true** si desea mostrar los comentarios; en caso contrario, **false**.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]

## <a name="see-also"></a>Vea también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Cómo: agregar y eliminar comentarios de hojas de cálculo mediante programación](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
