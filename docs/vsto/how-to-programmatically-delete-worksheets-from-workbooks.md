---
title: "C&#243;mo: Eliminar hojas de c&#225;lculo de libros mediante programaci&#243;n | Microsoft Docs"
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
  - "libros, eliminar hojas de cálculo"
  - "hojas de cálculo, eliminar"
ms.assetid: c5ae99f0-806d-4320-a29c-75ad444fb996
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# C&#243;mo: Eliminar hojas de c&#225;lculo de libros mediante programaci&#243;n
  Puede eliminar cualquier hoja de cálculo de un libro.  Para eliminar una hoja de cálculo, use el elemento host worksheet o acceda a la hoja de cálculo mediante la colección Sheets del libro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Usar el elemento host Worksheet  
 Si la hoja de cálculo se agregó en tiempo de diseño en una personalización de nivel de documento, use el método <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> para eliminar una hoja de cálculo especificada.  El siguiente código elimina una hoja de cálculo de un libro haciendo referencia directamente al elemento host worksheet.  
  
> [!IMPORTANT]  
>  Este código solo se ejecuta en proyectos creados mediante cualquiera de las siguientes plantillas de proyecto:  
>   
>  -   Libro de Excel 2013  
> -   Plantilla de Excel 2013  
> -   Libro de Excel 2010  
> -   Plantilla de Excel 2010  
>   
>  Si desea llevar a cabo esta tarea en cualquier otro tipo de proyecto, debe agregar una referencia al ensamblado **Microsoft.Office.Interop.Excel** y, después, debe usar las clases de dicho ensamblado para abrir un libro y eliminar una hoja de cálculo.  Para obtener más información, consulte [Cómo: Apuntar a las aplicaciones de Office mediante los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) y [Referencia de ensamblado de interoperabilidad primario de Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
#### Para eliminar una hoja de cálculo mediante un elemento host worksheet  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> de `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#17)]  
  
## Usar la colección Sheets del libro de Excel  
 Acceda a las hojas de cálculo a través de la colección <xref:Microsoft.Office.Interop.Excel.Sheets> de Microsoft Office Excel en los siguientes casos:  
  
-   Desea eliminar una hoja de cálculo de un complemento de VSTO.  
  
-   La hoja de cálculo que desea eliminar se creó en tiempo de ejecución en una personalización de nivel de documento.  
  
 El siguiente código elimina una hoja de cálculo de un libro haciendo referencia a la hoja a través del número de índice de la colección **Sheets**.  Este código supone que se ha creado una nueva hoja de cálculo mediante programación.  
  
> [!IMPORTANT]  
>  Si desea llevar a cabo esta tarea en cualquier otro tipo de proyecto, debe agregar una referencia al ensamblado **Microsoft.Office.Interop.Excel** y, después, debe usar las clases de dicho ensamblado para abrir un libro y eliminar una hoja de cálculo.  Para obtener más información, consulte [Cómo: Apuntar a las aplicaciones de Office mediante los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) y [Referencia de ensamblado de interoperabilidad primario de Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
#### Para eliminar una hoja de cálculo mediante la colección Sheets del libro de Excel  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> de la colección <xref:Microsoft.Office.Interop.Excel.Sheets>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#18)]  
  
## Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: Ocultar hojas de cálculo mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Cómo: Mover hojas de cálculo dentro de libros mediante programación](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Cómo: Seleccionar hojas de cálculo mediante programación](../vsto/how-to-programmatically-select-worksheets.md)   
 [Cómo: Agregar nuevas hojas de cálculo a libros mediante programación](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Elemento host Worksheet](../vsto/worksheet-host-item.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  