---
title: 'Cómo: proteger hojas de cálculo de mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 819a1f4e07397720d806d887408b9e45aeda9ea5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867187"
---
# <a name="how-to-programmatically-protect-worksheets"></a>Cómo: proteger hojas de cálculo de mediante programación
  La característica de protección de Microsoft Office Excel ayuda a evitar que los usuarios y el código modifiquen los objetos de una hoja de cálculo. De forma predeterminada, todas las celdas se bloquean después de activar la protección.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 En las personalizaciones de nivel de documento, puede proteger hojas de cálculo usando el diseñador de Excel. También puede proteger una hoja de cálculo mediante programación en tiempo de ejecución en cualquier tipo de proyecto.  
  
> [!NOTE]  
>  No puede agregar controles de Windows Forms a las áreas de una hoja de cálculo que están protegidas.  
  
## <a name="use-the-designer"></a>Use el diseñador  
  
### <a name="to-protect-a-worksheet-in-the-designer"></a>Para proteger una hoja de cálculo en el diseñador  
  
1. En el **cambios** grupo de la **revisión** , haga clic **Proteger hoja**.  
  
    El **Proteger hoja** aparece el cuadro de diálogo. Puede establecer una contraseña y, si lo desea, especificar algunas acciones que los usuarios pueden realizar en la hoja de cálculo, como, por ejemplo, dar formato a las celdas o insertar filas.  
  
   También puede permitir a los usuarios editar determinados rangos en hojas de cálculo protegidas.  
  
### <a name="to-allow-editing-in-specific-ranges"></a>Para permitir la modificación de rangos específicos  
  
1.  En el **cambios** grupo de la **revisión** , haga clic **permitir que los usuarios modifiquen rangos**.  
  
     El **permitir que los usuarios modifiquen rangos** aparece el cuadro de diálogo. Puede especificar rangos que se desbloqueen mediante una contraseña y usuarios que pueden editar rangos sin contraseña.  
  
## <a name="use-code-at-runtime"></a>Use el código en tiempo de ejecución  
 El siguiente código establece la contraseña (mediante la variable getPasswordFromUser, que contiene una contraseña obtenida del usuario) y solo permite la ordenación.  
  
### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>Para proteger una hoja de cálculo mediante código en una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> de la hoja de cálculo. En este ejemplo se da por supuesto que está trabajando con una hoja de cálculo denominada `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#27)]  
  
### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>Para proteger una hoja de cálculo mediante código en un complemento de VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> de la hoja de cálculo activa.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#17)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: quitar la protección de hojas de cálculo mediante programación](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)   
 [Cómo: proteger libros mediante programación](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Cómo: ocultar hojas de cálculo de mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Elemento host Worksheet](../vsto/worksheet-host-item.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  