---
title: Procedimiento Quitar la protección de hojas de cálculo mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ccf7de70c3ef741119ec22f8fa9bc76868a47030
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084224"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Procedimiento Quitar la protección de hojas de cálculo mediante programación
  Puede quitar mediante programación la protección de una hoja de cálculo de Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 En el ejemplo siguiente se usa la variable `getPasswordFromUser`, que contiene una contraseña obtenida del usuario.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Para desproteger una hoja de cálculo en una personalización de nivel de documento

1. Llame a la <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> método de la hoja de cálculo y pase la contraseña, si es necesario. En este ejemplo se da por supuesto que está trabajando con una hoja de cálculo denominada `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>Para desproteger una hoja de cálculo en un complemento de VSTO

1. Llame a la <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> método de la hoja de cálculo activa y pase la contraseña, si es necesario.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]

## <a name="see-also"></a>Vea también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Cómo: Proteger mediante programación las hojas de cálculo](../vsto/how-to-programmatically-protect-worksheets.md)
- [Cómo: Proteger libros mediante programación](../vsto/how-to-programmatically-protect-workbooks.md)
- [Cómo: Ocultar mediante programación las hojas de cálculo](../vsto/how-to-programmatically-hide-worksheets.md)
- [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
