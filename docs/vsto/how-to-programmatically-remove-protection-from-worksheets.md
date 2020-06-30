---
title: 'Cómo: quitar la protección de las hojas de cálculo mediante programación'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 72448f9d1e5c24c917459b8c2c59e317190e0a11
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85519878"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Cómo: quitar la protección de las hojas de cálculo mediante programación
  Puede quitar mediante programación la protección de una hoja de cálculo de Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 En el ejemplo siguiente se usa la variable `getPasswordFromUser`, que contiene una contraseña obtenida del usuario.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Para desproteger una hoja de cálculo en una personalización de nivel de documento

1. Llame al <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> método de la hoja de cálculo y pase la contraseña, si es necesario. En este ejemplo se da por supuesto que está trabajando con una hoja de cálculo denominada `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>Para desproteger una hoja de cálculo en un complemento de VSTO

1. Llame al <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> método de la hoja de cálculo activa y pase la contraseña, si es necesario.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]

## <a name="see-also"></a>Consulte también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Cómo: proteger hojas de cálculo mediante programación](../vsto/how-to-programmatically-protect-worksheets.md)
- [Cómo: proteger libros mediante programación](../vsto/how-to-programmatically-protect-workbooks.md)
- [Cómo: ocultar hojas de cálculo mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)
- [Acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
