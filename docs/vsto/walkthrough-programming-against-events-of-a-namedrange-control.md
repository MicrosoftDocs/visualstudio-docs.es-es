---
title: "Tutorial: Programar bas&#225;ndose en los eventos de un control NamedRange"
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
  - "NamedRange (control), eventos"
  - "intervalos, programar basándose en eventos"
  - "hojas de cálculo, automatización"
  - "hojas de cálculo, cambiar los valores de las celdas"
  - "hojas de cálculo, eventos"
ms.assetid: b69676f9-23b2-4ed6-83ab-8868c3f10948
caps.latest.revision: 57
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 56
---
# Tutorial: Programar bas&#225;ndose en los eventos de un control NamedRange
  En este tutorial, se muestra cómo agregar un control <xref:Microsoft.Office.Tools.Excel.NamedRange> a una hoja de cálculo de Microsoft Office Excel y cómo programar basándose en sus eventos mediante las herramientas de desarrollo de Office en Visual Studio.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante este tutorial aprenderá a:  
  
-   Agregar un control <xref:Microsoft.Office.Tools.Excel.NamedRange> a una hoja de cálculo.  
  
-   Programar basándose en los eventos del control <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
-   Probar el proyecto.  
  
> [!NOTE]  
>  Es posible que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que tenga y la configuración que esté usando determinan estos elementos.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Crear el proyecto  
 En este paso, creará un proyecto de libro de Excel con Visual Studio.  
  
#### Para crear un nuevo proyecto  
  
1.  Cree un proyecto de libro de Excel con el nombre Mis eventos de rango con nombre.  Asegúrese de que esté seleccionada la opción **Crear un nuevo documento**.  Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abrirá el nuevo libro de Excel en el diseñador y agregará el proyecto Mis eventos de rango con nombre al **Explorador de soluciones**.  
  
## Agregar texto y rangos con nombre a la hoja de cálculo  
 Los controles host son objetos de Office extendidos, por lo que puede agregarlos al documento del mismo modo que agregaría el objeto nativo.  Por ejemplo, puede agregar un control <xref:Microsoft.Office.Tools.Excel.NamedRange> de Excel a una hoja de cálculo si abre el menú **Insertar**, señala **Nombre** y elige **Definir**.  También puede agregar un control <xref:Microsoft.Office.Tools.Excel.NamedRange> arrastrándolo desde el **Cuadro de herramientas** hasta la hoja de cálculo.  
  
 En este paso, agregará dos controles de rango con nombre a la hoja de cálculo utilizando el **Cuadro de herramientas** y, a continuación, agregará texto a la hoja de cálculo.  
  
#### Para agregar un rango a la hoja de cálculo  
  
1.  Compruebe que el libro **El rango con nombre Events.xlsx** está abierto en el diseñador de Visual Studio, con `Sheet1` mostrados.  
  
2.  En la ficha **Controles de Excel** del Cuadro de herramientas, arrastre un control <xref:Microsoft.Office.Tools.Excel.NamedRange> a la celda **A1** de `Sheet1`.  
  
     Aparecerá el cuadro de diálogo **Agregar control NamedRange**.  
  
3.  Compruebe que en el cuadro de texto modificable aparece **$ A$1** y que la celda **A1** está seleccionada.  Si no lo está, haga clic en la celda **A1** para seleccionarla.  
  
4.  Haga clic en **Aceptar**.  
  
     La celda **A1** se convierte en un rango denominado `namedRange1`.  No hay ninguna indicación visible en la hoja de cálculo, pero en el cuadro **Nombre** \(situado sobre la hoja de cálculo en el lado izquierdo\) aparece `namedRange1` cuando se selecciona la celda **A1**.  
  
5.  Agregue otro control <xref:Microsoft.Office.Tools.Excel.NamedRange> a la celda **B3**.  
  
6.  Compruebe que en el cuadro de texto modificable aparece **$B$·** y que la celda **B3** está seleccionada.  Si no lo está, haga clic en la celda **B3** para seleccionarla.  
  
7.  Haga clic en **Aceptar**.  
  
     La celda **B3** se convierte en un rango denominado `namedRange2`.  
  
#### Para agregar texto a la hoja de cálculo  
  
1.  En la celda **A1**, escriba el texto siguiente:  
  
     Este es un ejemplo de control NamedRange.  
  
2.  En la celda **A3** \(a la izquierda de `namedRange2`\), escriba el texto siguiente:  
  
     Eventos:  
  
 En las secciones siguientes, escribirá código que inserta texto en `namedRange2` y modifica propiedades del control `namedRange2` en respuesta a los eventos <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> y <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> de `namedRange1`.  
  
## Agregar código para responder al evento BeforeDoubleClick  
  
#### Para insertar texto en NamedRange2 basado en el evento BeforeDoubleClick  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en **Sheet1.vb** o **Sheet1.cs** y elija **Ver código**.  
  
2.  Agregue código de modo que el controlador de eventos `namedRange1_BeforeDoubleClick` tenga el aspecto siguiente:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#24)]  
  
3.  En C\#, debe agregar controladores de eventos para los intervalos con nombre tal como se muestra a continuación en el evento <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>.  Para obtener información sobre la creación de controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#25)]  
  
## Agregar código para responder al evento Change  
  
#### Para insertar texto en namedRange2 basado en el evento Change  
  
1.  Agregue código de modo que el controlador de eventos `NamedRange1_Change` tenga el aspecto siguiente:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Cuando se hace doble clic en una celda de un rango de Excel, se activa el modo de edición; por tanto, cuando la selección se desplaza fuera del rango, se produce un evento <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>, incluso si no se producen cambios en el texto.  
  
## Agregar código para responder al evento SelectionChange  
  
#### Para insertar texto en namedRange2 basado en el evento SelectionChange  
  
1.  Agregue código de modo que el controlador de eventos **NamedRange1\_SelectionChange** tenga el aspecto siguiente:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Cuando se hace doble clic en una celda de un rango de Excel, la selección se desplaza al rango; por tanto, se produce un evento <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> antes del evento <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>.  
  
## Probar la aplicación  
 Ahora puede probar el libro para comprobar que el texto que describe los eventos de un control <xref:Microsoft.Office.Tools.Excel.NamedRange> se inserta en otro rango con nombre cuando se generan los eventos.  
  
#### Para probar el documento  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Coloque el cursor en `namedRange1` y compruebe que se inserta el texto relativo al evento <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> y que en la hoja de cálculo se incluye un comentario.  
  
3.  Haga doble clic dentro de `namedRange1` y compruebe que el texto relativo a los eventos <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> se inserta con texto rojo en cursiva en `namedRange2`.  
  
4.  Haga clic fuera de `namedRange1` y observe que se produce el evento Change al salir del modo de edición, aunque no se haya efectuado ningún cambio en el texto.  
  
5.  Cambie el texto de `namedRange1`.  
  
6.  Haga clic fuera de `namedRange1` y compruebe que el texto relativo al evento <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> se inserta con texto azul en `namedRange2`.  
  
## Pasos siguientes  
 Este tutorial muestra los fundamentos de la programación basada en eventos de un control <xref:Microsoft.Office.Tools.Excel.NamedRange>.  A continuación se indica una tarea que podría tener lugar a continuación:  
  
-   Implementar el proyecto.  Para obtener más información, vea [Implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
## Vea también  
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md)   
 [Cómo: Cambiar el tamaño de los controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Cómo: Agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  