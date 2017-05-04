---
title: "C&#243;mo: Proteger hojas de c&#225;lculo mediante programaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "protección de documentos, agregar a hojas de cálculo"
  - "documentos [desarrollo de Office en Visual Studio], protección de documentos"
  - "protección, agregar a hojas de cálculo"
  - "hojas de cálculo, proteger"
ms.assetid: 50bde1ff-918a-42ca-ba1b-f22139f8717a
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# C&#243;mo: Proteger hojas de c&#225;lculo mediante programaci&#243;n
  La característica de protección de Microsoft Office Excel ayuda a evitar que los usuarios y el código modifiquen los objetos de una hoja de cálculo.  De forma predeterminada, todas las celdas se bloquean después de activar la protección.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 En las personalizaciones de nivel de documento, puede proteger hojas de cálculo usando el diseñador de Excel.  También puede proteger una hoja de cálculo mediante programación en tiempo de ejecución en cualquier tipo de proyecto.  
  
> [!NOTE]  
>  No puede agregar controles de Windows Forms a las áreas de una hoja de cálculo que están protegidas.  
  
## Usar el diseñador  
  
#### Para proteger una hoja de cálculo en el diseñador  
  
1.  En el grupo **Cambios** de la pestaña **Revisión**, haga clic en **Proteger hoja**.  
  
     Se mostrará el cuadro de diálogo **Proteger hoja**.  Puede establecer una contraseña y, si lo desea, especificar algunas acciones que los usuarios pueden realizar en la hoja de cálculo, como, por ejemplo, dar formato a las celdas o insertar filas.  
  
 También puede permitir a los usuarios editar determinados rangos en hojas de cálculo protegidas.  
  
#### Para permitir la modificación de rangos específicos  
  
1.  En el grupo **Cambios** de la pestaña **Revisión**, haga clic en **Permitir que los usuarios modifiquen rangos hoja**.  
  
     Se mostrará el cuadro de diálogo **Permitir que los usuarios modifiquen rangos**.  Puede especificar rangos que se desbloqueen mediante una contraseña y usuarios que pueden editar rangos sin contraseña.  
  
## Usar código en tiempo de ejecución  
 El siguiente código establece la contraseña \(mediante la variable getPasswordFromUser, que contiene una contraseña obtenida del usuario\) y solo permite la ordenación.  
  
#### Para proteger una hoja de cálculo mediante código en una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> de la hoja de cálculo.  En este ejemplo se da por supuesto que está trabajando con una hoja de cálculo denominada `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomation#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#27)]  
  
#### Para proteger una hoja de cálculo mediante código en un complemento de VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> de la hoja de cálculo activa.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/CS/ThisAddIn.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomationAddIn/VB/ThisAddIn.vb#17)]  
  
## Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: Desproteger hojas de cálculo mediante programación](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)   
 [Cómo: Proteger libros mediante programación](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Cómo: Ocultar hojas de cálculo mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Elemento host Worksheet](../vsto/worksheet-host-item.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  