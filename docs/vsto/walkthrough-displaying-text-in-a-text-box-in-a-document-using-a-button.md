---
title: "Tutorial: Mostrar texto en un cuadro de texto en un documento utilizando un bot&#243;n | Microsoft Docs"
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
  - "cuadros de texto, mostrar texto en documentos"
ms.assetid: 04c54ed7-9f00-4068-aaec-1f3200110116
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Tutorial: Mostrar texto en un cuadro de texto en un documento utilizando un bot&#243;n
  Este tutorial muestra cómo usar los botones y cuadros de texto en una personalización de nivel de documento para Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Agregar controles al documento Word en un proyecto de nivel de documento en tiempo de diseño.  
  
-   Rellenar un cuadro de texto cuando se hace clic en un botón.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## Crear el proyecto  
 El primer paso es crear un proyecto de tipo Documento de Word.  
  
#### Para crear un nuevo proyecto  
  
1.  Cree un proyecto de Documento de Word con el nombre Mi botón de Word.  En el asistente, seleccione **Crear un nuevo documento**.  
  
     Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo documento de Word en el diseñador y agrega el proyecto **Mi botón de Word** al **Explorador de soluciones**.  
  
## Agregar controles al documento de Word  
 Los controles de interfaz de usuario están compuestos por un botón y un cuadro de texto en el documento de Word.  
  
#### Para agregar un botón y un cuadro de texto  
  
1.  Compruebe que el documento esté abierto en el diseñador de Visual Studio.  
  
2.  Desde la pestaña **Controles comunes** del **Cuadro de herramientas**, arrastre un control <xref:Microsoft.Office.Tools.Word.Controls.TextBox> hasta el documento.  
  
    > [!NOTE]  
    >  En Word, los controles se colocan de forma predeterminada en línea con el texto.  Puede modificar la forma en la que se insertan los controles y los objetos de forma cambiando el valor predeterminado en la pestaña **Editar** del cuadro de diálogo **Opciones** de Word.  
  
3.  En el menú **Ver**, haga clic en la **Ventana Propiedades**.  
  
4.  Busque **TextBox1** en el cuadro desplegable de la ventana **Propiedades** y cambie la propiedad **Name** del cuadro de texto **displayText**.  
  
5.  Arrastre un control **Button** hasta el documento y cambie las siguientes propiedades.  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Nombre**|**insertText**|  
    |**Texto**|Insertar texto|  
  
 Ahora puede escribir el código que se ejecutará cuando se haga clic en el botón.  
  
## Rellenar un cuadro de texto cuando se hace clic en el botón  
 Cada vez que el usuario haga clic en el botón, se agregará **Hello World\!** al cuadro de texto.  
  
#### Para escribir en el cuadro de texto cuando se haga clic en el botón  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en **ThisDocument** y, a continuación, haga clic en **Ver código** en el menú contextual.  
  
2.  Agregue el siguiente código al controlador de eventos <xref:System.Windows.Forms.Control.Click> del botón.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#7)]  
  
3.  En C\#, debe agregar un controlador de eventos para el botón al evento <xref:Microsoft.Office.Tools.Word.Document.Startup>.  Para obtener información sobre cómo crear controladores de eventos, consulte [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#8)]  
  
## Probar la aplicación  
 Ahora puede probar el documento para asegurarse de que se muestre el mensaje **Hello World\!** en el cuadro de texto al hacer clic en el botón.  
  
#### Para probar el documento  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Haga clic en el botón.  
  
3.  Confirme que se muestra **Hello World\!** en el cuadro de texto.  
  
## Pasos siguientes  
 Este tutorial muestra los conceptos básicos del uso de botones y cuadros de texto en documentos de Word.  A continuación, podría realizar las siguientes tareas:  
  
-   Usar un cuadro combinado para cambiar el formato.  Para obtener más información, consulte [Tutorial: Cambiar el formato de un documento utilizando controles CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
-   Usar botones de radio para seleccionar estilos de gráfico.  Para obtener más información, consulte [Tutorial: Actualizar un gráfico en un documento utilizando botones de radio](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## Vea también  
 [Información general sobre controles de formularios Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Tutoriales para Word](../vsto/walkthroughs-using-word.md)   
 [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Cómo: Agregar controles de Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)  
  
  