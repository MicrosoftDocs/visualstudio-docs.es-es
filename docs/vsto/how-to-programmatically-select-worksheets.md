---
title: 'Cómo: seleccionar hojas de cálculo de mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 09e477d802b9d92ca4f9e1cd3a532145ad0e68a0
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675542"
---
# <a name="how-to-programmatically-select-worksheets"></a>Cómo: seleccionar hojas de cálculo de mediante programación
  El método <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> selecciona el objeto especificado, que mueve la selección del usuario al nuevo objeto. Use el método <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> si desea llevar el foco al objeto sin cambiar la selección del usuario.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Si desea seleccionar una hoja de cálculo existente en un complemento de VSTO o si se ha creado la hoja de cálculo en tiempo de ejecución en una personalización de nivel de documento, debe tener acceso a él mediante el uso de Excel <xref:Microsoft.Office.Interop.Excel.Sheets> colección del libro de Excel; en caso contrario, puede tener acceso a la <xref:Microsoft.Office.Tools.Excel.Worksheet>directamente el elemento de host.  
  
## <a name="use-the-worksheet-host-item"></a>Utilice el elemento host worksheet  
 En una personalización de nivel de documento, agregue el código siguiente al *Sheet1.vb* o *Sheet1.cs*.  
  
### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Para seleccionar la primera hoja de cálculo en un libro usando un elemento host  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> de `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]  
  
## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Usar la colección sheets del libro de Excel  
 Acceda a la hoja de cálculo mediante la colección <xref:Microsoft.Office.Interop.Excel.Sheets> de Excel.  
  
### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Para seleccionar la primera hoja de cálculo de un libro mediante la colección Sheets del libro de Excel  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> de la colección <xref:Microsoft.Office.Interop.Excel.Sheets> para seleccionar la primera hoja de cálculo del libro activo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: imprimir mediante programación las hojas de cálculo](../vsto/how-to-programmatically-print-worksheets.md)   
 [Cómo: eliminar hojas de cálculo de libros mediante programación](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Cómo: ocultar hojas de cálculo de mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Cómo: proteger hojas de cálculo de mediante programación](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Elemento host Worksheet](../vsto/worksheet-host-item.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)  
  
  