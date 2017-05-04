---
title: "Tutorial: Mostrar texto en un cuadro de texto en una hoja de c&#225;lculo utilizando un bot&#243;n | Microsoft Docs"
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
  - "texto [desarrollo de Office en Visual Studio], mostrar hojas de cálculo"
  - "texto [desarrollo de Office en Visual Studio], cuadros de texto"
  - "cuadros de texto, mostrar texto en hojas de cálculo"
  - "hojas de cálculo, mostrar texto"
ms.assetid: 59b73159-aab7-4f61-9ace-1723c18d78d6
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# Tutorial: Mostrar texto en un cuadro de texto en una hoja de c&#225;lculo utilizando un bot&#243;n
  En este tutorial se muestran aspectos básicos del uso de los botones y cuadros de texto en las hojas de cálculo de Microsoft Office Excel, así como de la creación de proyectos de Excel mediante las herramientas de desarrollo de Office en Visual Studio.  Para ver el resultado como un ejemplo completo, vea el ejemplo Excel Controls en [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante este tutorial aprenderá a:  
  
-   Agregar controles a una hoja de cálculo.  
  
-   Rellenar un cuadro de texto al hacer clic en un botón.  
  
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
  
1.  Cree un proyecto de libro de Excel con el nombre Mi botón de Excel.  Asegúrese de que esté seleccionada la opción **Crear un nuevo documento**.  Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto **Mi botón de Excel** al **Explorador de soluciones**.  
  
## Agregar controles a la hoja de cálculo  
 Para este tutorial, necesitará un botón y un cuadro de texto en la primera hoja de cálculo.  
  
#### Para agregar un botón y un cuadro de texto  
  
1.  Compruebe que el libro **Mis Excel Button.xlsx** está abierto en el diseñador de Visual Studio, con `Sheet1` mostrados.  
  
2.  Desde la ficha **Controles comunes** del Cuadro de herramientas, arrastre un control <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> hasta `Sheet1`.  
  
3.  En el menú **Ver**, seleccione **Ventana Propiedades**.  
  
4.  Asegúrese de que **TextBox1** se ve en la lista desplegable de la ventana **Propiedades** y cambie la propiedad **Name** del cuadro de texto a **displayText**.  
  
5.  Arrastre un control **Button** a `Sheet1` y cambie las siguientes propiedades:  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**insertText**|  
    |**Texto**|Insert Text|  
  
 A continuación, escriba el código que se va a ejecutar al hacer clic en el botón.  
  
## Rellenar el cuadro de texto al hacer clic en el botón  
 Cada vez que el usuario hace clic en el botón, **Hola a todos\!** se anexa al cuadro de texto.  
  
#### Para escribir en el cuadro de texto al hacer clic en el botón  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en **Sheet1** y, a continuación, haga clic en **Ver código** en el menú contextual.  
  
2.  Agregue el código siguiente al controlador de eventos <xref:System.Windows.Forms.Control.Click> del botón:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#11)]  
  
3.  En C\#, debe agregar un controlador de eventos al evento <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> como se muestra a continuación.  Para obtener información sobre la creación de controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#12)]  
  
## Probar la aplicación  
 Ahora puede probar el libro para asegurarse de que el mensaje **Hola a todos\!** aparece en el cuadro de texto al hacer clic en el botón.  
  
#### Para probar el libro  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Haga clic en el botón.  
  
3.  Confirme que **Hola a todos\!** aparece en el cuadro de texto.  
  
## Pasos siguientes  
 En este tutorial se muestran los aspectos básicos del uso de los botones y los cuadros de texto en las hojas de cálculo de Excel.  Éstas son algunas de las tareas que pueden venir a continuación:  
  
-   Implementar el proyecto.  Para obtener más información, vea [Implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
-   Utilizar casillas para cambiar el formato.  Para obtener más información, vea [Tutorial: Cambiar el formato de una hoja de cálculo utilizando controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## Vea también  
 [Cómo: Agregar controles de Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Tutoriales para Excel](../vsto/walkthroughs-using-excel.md)   
 [Limitaciones de los controles de formularios Windows Forms en los documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  