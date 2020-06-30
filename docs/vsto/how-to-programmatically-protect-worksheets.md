---
title: 'Cómo: proteger hojas de cálculo mediante programación'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d51a6557b2204d7b6ff3d8865c82de091f5a59d0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545904"
---
# <a name="how-to-programmatically-protect-worksheets"></a>Cómo: proteger hojas de cálculo mediante programación
  La característica de protección de Microsoft Office Excel ayuda a evitar que los usuarios y el código modifiquen los objetos de una hoja de cálculo. De forma predeterminada, todas las celdas se bloquean después de activar la protección.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 En las personalizaciones de nivel de documento, puede proteger hojas de cálculo usando el diseñador de Excel. También puede proteger una hoja de cálculo mediante programación en tiempo de ejecución en cualquier tipo de proyecto.

> [!NOTE]
> No puede agregar controles de Windows Forms a las áreas de una hoja de cálculo que están protegidas.

## <a name="use-the-designer"></a>Uso del diseñador

### <a name="to-protect-a-worksheet-in-the-designer"></a>Para proteger una hoja de cálculo en el diseñador

1. En el grupo **cambios** de la pestaña **revisión** , haga clic en **proteger hoja**.

    Aparece el cuadro de diálogo **proteger hoja** . Puede establecer una contraseña y, si lo desea, especificar algunas acciones que los usuarios pueden realizar en la hoja de cálculo, como, por ejemplo, dar formato a las celdas o insertar filas.

   También puede permitir a los usuarios editar determinados rangos en hojas de cálculo protegidas.

### <a name="to-allow-editing-in-specific-ranges"></a>Para permitir la modificación de rangos específicos

1. En el grupo **cambios** de la pestaña **revisar** , haga clic en **permitir a los usuarios editar rangos**.

     Aparece el cuadro de diálogo **permitir que los usuarios editen rangos** . Puede especificar rangos que se desbloqueen mediante una contraseña y usuarios que pueden editar rangos sin contraseña.

## <a name="use-code-at-run-time"></a>Usar código en tiempo de ejecución
 El siguiente código establece la contraseña (mediante la variable getPasswordFromUser, que contiene una contraseña obtenida del usuario) y solo permite la ordenación.

### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>Para proteger una hoja de cálculo mediante código en una personalización de nivel de documento

1. Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> de la hoja de cálculo. En este ejemplo se da por supuesto que está trabajando con una hoja de cálculo denominada `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#27)]

### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>Para proteger una hoja de cálculo mediante código en un complemento de VSTO

1. Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> de la hoja de cálculo activa.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#17)]

## <a name="see-also"></a>Consulte también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Cómo: quitar la protección de las hojas de cálculo mediante programación](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)
- [Cómo: proteger libros mediante programación](../vsto/how-to-programmatically-protect-workbooks.md)
- [Cómo: ocultar hojas de cálculo mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Elemento host de hoja de cálculo](../vsto/worksheet-host-item.md)
- [Acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
