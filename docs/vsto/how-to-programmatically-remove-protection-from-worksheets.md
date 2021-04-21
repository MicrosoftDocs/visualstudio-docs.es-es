---
title: 'Cómo: Quitar la protección de hojas de cálculo mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio quitar la protección de una hoja de cálculo de Microsoft Excel mediante programación.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c392ee3434edf9211a4a3061e7a83a8621960430
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824164"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Cómo: Quitar la protección de hojas de cálculo mediante programación
  Puede quitar mediante programación la protección de una hoja de cálculo de Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 En el ejemplo siguiente se usa la variable `getPasswordFromUser`, que contiene una contraseña obtenida del usuario.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Para desproteger una hoja de cálculo en una personalización de nivel de documento

1. Llame al <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> método de la hoja de cálculo y pase la contraseña, si es necesario. En este ejemplo se da por supuesto que está trabajando con una hoja de cálculo denominada `Sheet1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet28":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet28":::

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>Para desproteger una hoja de cálculo en un complemento de VSTO

1. Llame al <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> método de la hoja de cálculo activa y pase la contraseña, si es necesario.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet18":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet18":::

## <a name="see-also"></a>Consulte también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Cómo: Proteger hojas de cálculo mediante programación](../vsto/how-to-programmatically-protect-worksheets.md)
- [Cómo: Proteger libros mediante programación](../vsto/how-to-programmatically-protect-workbooks.md)
- [Cómo: Ocultar hojas de cálculo mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)
- [Acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
