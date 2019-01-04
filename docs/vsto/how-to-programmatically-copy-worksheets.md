---
title: Procedimiento Copiar mediante programación las hojas de cálculo
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a123191afe2a6aef18e9a4bc64f5bc966db6c479
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871309"
---
# <a name="how-to-programmatically-copy-worksheets"></a>Procedimiento Copiar mediante programación las hojas de cálculo
  Puede crear una copia de una hoja de cálculo e insertarla antes o después de otra hoja existente en el libro. Si no especifica dónde insertarla, Excel crea un nuevo libro para la nueva hoja de cálculo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Tanto si copia la hoja de cálculo mediante programación como si el usuario final copia la hoja de cálculo manualmente, no hay ningún código detrás de la nueva hoja de cálculo y los controles de la nueva hoja de cálculo no funcionan. Esto se debe a que la hoja de cálculo recién copiada es un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> y no un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet>. Los controles de Windows Forms y los controles host solo pueden agregarse a elementos host. Para obtener más información, consulte [limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Para agregar una hoja de cálculo copiada a un libro en una personalización de nivel de documento  
  
1.  Use el método <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> para copiar la primera hoja de cálculo en el libro actual y colocarla tras la tercera hoja.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]  
  
## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Para agregar una hoja de cálculo copiada a un libro en un complemento de VSTO  
  
1.  Use el método <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> para copiar la primera hoja de cálculo en el libro actual y colocarla tras la tercera hoja.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Cómo: Agregar nuevas hojas de cálculo a libros mediante programación](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Cómo: Eliminar hojas de cálculo de libros mediante programación](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Cómo: Seleccionar mediante programación las hojas de cálculo](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
