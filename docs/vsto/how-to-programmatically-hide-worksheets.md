---
title: "Cómo: ocultar hojas de cálculo de mediante programación | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1ce83d6cec246a5a232026dff4e11f3dc1ed9e06
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-hide-worksheets"></a>Cómo: Ocultar hojas de cálculo mediante programación
  Puede mostrar u ocultar las hojas de cálculo de un libro. Para ocultar una hoja de cálculo, use el elemento host de la hoja de cálculo o acceda a ella mediante la colección “Sheets” del libro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-the-worksheet-host-item"></a>Usar el elemento host Worksheet  
 Si la hoja de cálculo se agregó durante el diseño de una personalización de nivel de documento, use la propiedad <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> para ocultar la hoja de cálculo especificada.  
  
#### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>Ocultar una hoja de cálculo mediante un elemento host de hoja de cálculo  
  
1.  Establezca la propiedad <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> del elemento host `Sheet1` en el valor de la enumeración <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#25)]  
  
## <a name="using-the-sheets-collection-of-the-excel-workbook"></a>Usar la colección Sheets del libro de Excel  
 Acceda a las hojas de cálculo a través de la colección <xref:Microsoft.Office.Interop.Excel.Sheets> de Microsoft Office Excel en los siguientes casos:  
  
-   Si desea ocultar la hoja de cálculo de un complemento VSTO.  
  
-   Si la hoja de cálculo que desea ocultar se creó en tiempo de ejecución en una personalización de nivel de documento.  
  
#### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Ocultar una hoja de cálculo mediante la colección “Sheets” del libro de Excel  
  
1.  Establezca la propiedad <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> de la hoja de cálculo en el valor de enumeración <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#26)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: eliminar hojas de cálculo mediante programación de los libros](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Cómo: mover hojas de cálculo dentro de los libros de programación](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Cómo: proteger hojas de cálculo de mediante programación](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)  
  