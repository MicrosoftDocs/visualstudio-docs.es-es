---
title: "Tutorial: Cambiar el formato de una hoja de c&#225;lculo utilizando controles CheckBox | Microsoft Docs"
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
  - "controles [desarrollo de Office en Visual Studio], agregar a hojas de cálculo"
  - "hojas de cálculo, cambiar el formato utilizando controles administrados"
  - "hojas de cálculo, controles de casilla"
ms.assetid: 4be79613-50a0-428e-9816-aadbc098272a
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Tutorial: Cambiar el formato de una hoja de c&#225;lculo utilizando controles CheckBox
  En este tutorial se muestran los aspectos básicos del uso de las casillas en una hoja de cálculo de Microsoft Office Excel para cambiar el formato.  Utilizará las herramientas de desarrollo de Office en Visual Studio para crear y agregar código a un proyecto.  Para ver el resultado como un ejemplo completo, vea el ejemplo Excel Controls en [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante este tutorial aprenderá a:  
  
-   Agregar texto y controles a una hoja de cálculo.  
  
-   Aplicar formato al texto al seleccionar una opción.  
  
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
  
1.  Cree un proyecto de libro de Excel con el nombre Mi formato de Excel.  Asegúrese de que esté seleccionada la opción **Crear un nuevo documento**.  Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto **Mi formato de Excel** al **Explorador de soluciones**.  
  
## Agregar texto y controles a la hoja de cálculo  
 Para este tutorial, necesitará tres controles <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> y algo de texto en un control <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
#### Para agregar tres casillas  
  
1.  Compruebe que el libro está abierto en el diseñador de Visual Studio y que se ha abierto `Sheet1`.  
  
2.  Desde la ficha **Controles comunes** del **Cuadro de herramientas**, arrastre un control <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> a la celda **B2** o cerca de ella en **Sheet1**.  
  
3.  En el menú **Ver**, seleccione la ventana **Propiedades**.  
  
4.  Asegúrese de que **Checkbox1** es visible en el cuadro de lista del nombre de objeto en la ventana **Propiedades** y cambie las propiedades siguientes:  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**applyBoldFont**|  
    |**Texto**|Negrita|  
  
5.  Arrastre una segunda casilla a la celda **B4** o cerca de ella y cambie las siguientes propiedades:  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**applyItalicFont**|  
    |**Texto**|Cursiva|  
  
6.  Arrastre una tercera casilla a la celda **B6** o cerca de ella y cambie las siguientes propiedades:  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**applyUnderlineFont**|  
    |**Texto**|Subrayado|  
  
7.  Seleccione los tres controles de casilla mientras mantiene presionada la tecla CTRL.  
  
8.  En el grupo de organización de la pestaña de formato en Excel, haga clic **Alinear**, y haga clic en **Alinear a la izquierda**.  
  
     Los tres controles de casilla se alinean a la izquierda, en la posición del primer control seleccionado.  
  
     Luego, arrastrará un control <xref:Microsoft.Office.Tools.Excel.NamedRange> hasta la hoja de cálculo.  
  
    > [!NOTE]  
    >  También puede agregar el control <xref:Microsoft.Office.Tools.Excel.NamedRange> si escribe **textFont** en el cuadro **Nombre**.  
  
#### Para agregar texto a un control NamedRange  
  
1.  Desde la ficha **Controles de Excel** del cuadro de herramientas, arrastre un control <xref:Microsoft.Office.Tools.Excel.NamedRange> hasta la celda **B9**.  
  
2.  Compruebe que aparece **$B$9** en el cuadro de texto modificable y que está seleccionada la celda **B9**.  Si no lo está, haga clic en la celda **B9** para seleccionarla.  
  
3.  Haga clic en **Aceptar**.  
  
4.  La celda **B9** se convierte en un rango denominado `NamedRange1`.  
  
     No hay ninguna indicación visible en la hoja de cálculo, pero aparece `NamedRange1` en el cuadro **Nombre** \(justo encima de la hoja de cálculo, en el lado izquierdo\) cuando se selecciona la celda **B9**.  
  
5.  Asegúrese de que **NamedRange1** es visible en el cuadro de lista de nombre del objeto de la ventana **Propiedades** y cambie las propiedades siguientes:  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**textFont**|  
    |**Value2**|Haga clic en una casilla para cambiar el formato de este texto.|  
  
 A continuación, escriba el código para dar formato al texto al seleccionar una opción.  
  
## Aplicar formato al texto al seleccionar una opción  
 En esta sección escribirá código para que, cuando el usuario seleccione una opción de formato, se cambie el formato del texto en la hoja de cálculo.  
  
#### Para cambiar el formato cuando se activa una casilla  
  
1.  Haga clic con el botón secundario del mouse en **Sheet1** y, a continuación, haga clic en **Ver código** en el menú contextual.  
  
2.  Agregue el código siguiente al controlador de eventos <xref:System.Windows.Forms.Control.Click> de la casilla `applyBoldFont`:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#7)]  
  
3.  Agregue el código siguiente al controlador de eventos <xref:System.Windows.Forms.Control.Click> de la casilla `applyItalicFont`:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#8)]  
  
4.  Agregue el código siguiente al controlador de eventos <xref:System.Windows.Forms.Control.Click> de la casilla `applyUnderlineFont`:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#9)]  
  
5.  En C\#, debe agregar controladores de eventos para las casillas al evento <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> tal y como se indica a continuación.  Para obtener información sobre la creación de controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#10)]  
  
## Probar la aplicación  
 Ahora puede probar el libro para asegurarse de que se aplica el formato correcto al texto cuando se activa o se desactiva una casilla.  
  
#### Para probar el libro  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Active o desactive una casilla.  
  
3.  Confirme que el texto tiene el formato correcto.  
  
## Pasos siguientes  
 En este tutorial se muestran los aspectos básicos del uso de las casillas y la aplicación de formato a texto en hojas de cálculo de Excel.  Éstas son algunas de las tareas que pueden venir a continuación:  
  
-   Implementar el proyecto.  Para obtener más información, vea [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
-   Utilizar un botón para rellenar un cuadro de texto.  Para obtener más información, vea [Tutorial: Mostrar texto en un cuadro de texto en una hoja de cálculo utilizando un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## Vea también  
 [Tutoriales para Excel](../vsto/walkthroughs-using-excel.md)   
 [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md)   
 [Limitaciones de los controles de formularios Windows Forms en los documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  