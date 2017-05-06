---
title: "C&#243;mo: Cambiar el tama&#241;o de los controles NamedRange"
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
  - "controles [desarrollo de Office en Visual Studio] cambiar tamaño"
  - "NamedRange (control), cambiar tamaño"
  - "rangos, cambiar tamaño en Excel"
ms.assetid: 7d6f0b2f-be46-49b7-9f38-b4c8849683f7
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# C&#243;mo: Cambiar el tama&#241;o de los controles NamedRange
  Aunque se puede establecer el tamaño de un control <xref:Microsoft.Office.Tools.Excel.NamedRange> al agregarlo a un documento de Microsoft Office Excel, podrían ser necesarios cambios posteriores.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 En proyectos de nivel de documento, el tamaño de un rango con nombre se puede cambiar en tiempo de diseño o en tiempo de ejecución También se puede cambiar su tamaño en tiempo de ejecución en los complementos de VSTO de nivel de aplicación.  
  
 En este tema se describen las tareas siguientes:  
  
-   [Cambiar el tamaño de los controles NamedRange en tiempo de diseño](#designtime)  
  
-   [Cambiar el tamaño de los controles NamedRange en tiempo de ejecución en un proyecto de nivel de documento](#runtimedoclevel)  
  
-   [Cambiar el tamaño de los controles NamedRange en tiempo de ejecución en un proyecto de complemento de VSTO](#runtimeaddin)  
  
##  <a name="designtime"></a> Cambiar el tamaño de los controles NamedRange en tiempo de diseño  
 Para cambiar el tamaño de un rango con nombre, es necesario volver a definir el tamaño en el cuadro de diálogo **Definir nombre**.  
  
#### Para cambiar el tamaño de un rango con nombre mediante el cuadro de diálogo Definir nombre  
  
1.  Haga clic en un control <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
2.  Haga clic en **Administrar rangos con nombre** en el menú contextual.  
  
     Se mostrará el cuadro de diálogo **Definir nombre**.  
  
3.  Seleccione el rango con nombre cuyo tamaño quiere cambiar.  
  
4.  Desactive el cuadro **Se refiere a**.  
  
5.  Seleccione las celdas que quiere usar para definir el tamaño del rango con nombre.  
  
6.  Haga clic en **Aceptar**.  
  
##  <a name="runtimedoclevel"></a> Cambiar el tamaño de los controles NamedRange en tiempo de ejecución en un proyecto de nivel de documento  
 Este tamaño se puede cambiar mediante programación, con la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A>.  
  
> [!NOTE]  
>  En la ventana **Propiedades**, la propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> se marca como de solo lectura.  
  
#### Para cambiar el tamaño de un rango con nombre mediante programación  
  
1.  Cree un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en la celda **A1** de `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#4)]  
  
2.  Cambie el tamaño del rango con nombre para incluir la celda **B1**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#5)]  
  
##  <a name="runtimeaddin"></a> Cambiar el tamaño de los controles NamedRange en tiempo de ejecución en un proyecto de complemento de VSTO  
 Se puede cambiar el tamaño de un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en tiempo de ejecución en cualquier hoja de cálculo abierta. Para obtener más información sobre cómo agregar un control <xref:Microsoft.Office.Tools.Excel.NamedRange> a una hoja de cálculo mediante un complemento de VSTO, consulte [Cómo: Agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
#### Para cambiar el tamaño de un rango con nombre mediante programación  
  
1.  Cree un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en la celda **A1** de `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#10)]  
  
2.  Cambie el tamaño del rango con nombre para incluir la celda **B1**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#11)]  
  
## Vea también  
 [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md)   
 [Cómo: Agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Cómo: Cambiar el tamaño de los controles Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Cómo: Cambiar el tamaño de los controles ListObject](../vsto/how-to-resize-listobject-controls.md)  
  
  