---
title: "Tutorial: Automatizar una aplicaci&#243;n desde un panel de tareas personalizado"
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
  - "paneles de tareas [desarrollo de Office en Visual Studio], PowerPoint"
  - "PowerPoint [desarrollo de Office en Visual Studio], paneles de tareas personalizados"
  - "automatizar aplicaciones de Office"
  - "paneles de tareas personalizados [desarrollo de Office en Visual Studio], automatizar aplicaciones"
  - "paneles de tareas personalizados [desarrollo de Office en Visual Studio], PowerPoint"
  - "paneles de tareas [desarrollo de Office en Visual Studio], automatizar aplicaciones"
ms.assetid: 77be5ab5-e330-4564-87ec-9cba564ba8f9
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Tutorial: Automatizar una aplicaci&#243;n desde un panel de tareas personalizado
  En este tutorial se muestra cómo crear un panel de tareas personalizado que automatiza PowerPoint. El panel de tareas personalizado inserta fechas en una diapositiva cuando el usuario hace clic en un control <xref:System.Windows.Forms.MonthCalendar> que se encuentra en el panel de tareas personalizado.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 Aunque este tutorial usa PowerPoint de manera específica, los conceptos que se muestran en el tutorial son aplicables a cualquier aplicación que se muestre arriba.  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Diseño de la interfaz de usuario del panel de tareas personalizado.  
  
-   Automatización de PowerPoint desde el panel de tareas personalizado.  
  
-   Visualización del panel de tareas personalizado en PowerPoint.  
  
> [!NOTE]  
>  Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para obtener más información, vea [Personalización de la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft PowerPoint 2010 o [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)].  
  
## Crear el proyecto del complemento  
 El primer paso es crear un proyecto de complemento VSTO para PowerPoint.  
  
#### Para crear un nuevo proyecto  
  
1.  Cree un proyecto de complemento de VSTO de PowerPoint con el nombre **MyAddIn**, usando la plantilla de proyecto de complemento de PowerPoint. Para obtener más información, consulta [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre el archivo de código **ThisAddIn.cs** o **ThisAddIn.vb** y agrega el proyecto **MyAddIn** al **Explorador de soluciones**.  
  
## Diseñar la interfaz de usuario del panel de tareas personalizado  
 No hay ningún diseñador visual para los paneles de tareas personalizados, pero puede diseñar un control de usuario con el diseño que quiera. Más adelante en este tutorial, agregará el control de usuario al panel de tareas personalizado.  
  
#### Para diseñar la interfaz de usuario del panel de tareas personalizado  
  
1.  En el menú **Proyecto**, haga clic en **Agregar control de usuario**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento**, cambie el nombre del control de usuario a **MyUserControl** y haga clic en **Agregar**.  
  
     Se abre el control de usuario en el diseñador.  
  
3.  En la pestaña **Controles comunes** de **Cuadro de herramientas**, arrastre un control **MonthCalendar** al control del usuario.  
  
     Si el control **MonthCalendar** es mayor que la superficie de diseño del control de usuario, cambie el tamaño del control del usuario para ajustar el control **MonthCalendar**.  
  
## Automatizar PowerPoint desde el panel de tareas personalizado  
 El propósito del complemento de VSTO es poner una fecha seleccionada en la primera diapositiva de la presentación activa. Use el evento <xref:System.Windows.Forms.MonthCalendar.DateChanged> del control para agregar la fecha seleccionada cada vez que cambie.  
  
#### Para automatizar PowerPoint desde el panel de tareas personalizado  
  
1.  En el diseñador, haga doble clic en el control <xref:System.Windows.Forms.MonthCalendar>.  
  
     Se abre el archivo **MyUserControl.cs** o **MyUserControl.vb** y se crea un controlador de eventos para el evento <xref:System.Windows.Forms.MonthCalendar.DateChanged>.  
  
2.  Agregue el código siguiente a la parte superior del archivo. Este código crea un alias para los espacios de nombres <xref:Microsoft.Office.Core> y <xref:Microsoft.Office.Interop.PowerPoint>.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/MyUserControl.vb#1)]  
  
3.  Agregue el código siguiente a la clase `MyUserControl`. Este código declara un objeto <xref:Microsoft.Office.Interop.PowerPoint.Shape> como miembro de `MyUserControl`. En el siguiente paso, usará este <xref:Microsoft.Office.Interop.PowerPoint.Shape> para agregar un cuadro de texto a una diapositiva de la presentación activa.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/MyUserControl.vb#2)]  
  
4.  Reemplace el controlador de eventos `monthCalendar1_DateChanged` por el siguiente código: Este código agrega un cuadro de texto a la primera diapositiva de la presentación activa y luego agrega la fecha seleccionada al cuadro de texto. Este código usa el objeto `Globals.ThisAddIn` para tener acceso al modelo de objetos de PowerPoint.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/MyUserControl.vb#3)]  
  
5.  En el **Explorador de soluciones**, haga clic con el botón secundario en el proyecto **MyAddIn** y luego haga clic en **Crear**. Compruebe que el proyecto se compila sin errores.  
  
## Visualización del panel de tareas personalizado  
 Para mostrar el panel de tareas personalizado cuando se inicia el complemento de VSTO, agregue el control de usuario al panel de tareas en el controlador de eventos <xref:Microsoft.Office.Tools.AddIn.Startup> del complemento de VSTO.  
  
#### Para visualizar el panel de tareas personalizado  
  
1.  En el **Explorador de soluciones**, expanda **PowerPoint**.  
  
2.  Haga clic en **ThisAddIn.cs** o **ThisAddIn.vb**, y luego en **Ver código**.  
  
3.  Agregue el código siguiente a la clase `ThisAddIn`. Este código declara instancias de `MyUserControl` y <xref:Microsoft.Office.Tools.CustomTaskPane> como miembros de la clase `ThisAddIn`.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneMonthCalendar#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/ThisAddIn.vb#4)]  
  
4.  Reemplace el controlador de eventos `ThisAddIn_Startup` por el siguiente código: Este código crea un nuevo <xref:Microsoft.Office.Tools.CustomTaskPane> agregando el objeto `MyUserControl` a la colección `CustomTaskPanes`. El código también muestra el panel de tareas.  
  
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_TaskPaneMonthCalendar#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneMonthCalendar/VB/ThisAddIn.vb#5)]  
  
## Probar el complemento  
 Al ejecutar el proyecto, se abre PowerPoint y el complemento de VSTO muestra el panel de tareas personalizado. Haga clic en el control <xref:System.Windows.Forms.MonthCalendar> para probar el código.  
  
#### Para probar el complemento de VSTO  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Confirme que el panel de tareas personalizado está visible.  
  
3.  Haga clic en una fecha en el control <xref:System.Windows.Forms.MonthCalendar> del panel de tareas.  
  
     La fecha se inserta en la primera diapositiva de la presentación activa.  
  
## Pasos siguientes  
 En estos temas puede obtener más información sobre cómo crear paneles de tareas personalizados:  
  
-   Cree un panel de tareas personalizado en un complemento de VSTO para una aplicación diferente. Para obtener más información sobre las aplicaciones que admiten paneles de tareas personalizados, vea [Paneles de tareas personalizados](../vsto/custom-task-panes.md).  
  
-   Crear un botón de la cinta de opciones que se pueda usar para ocultar o mostrar un panel de tareas personalizado. Para obtener más información, consulta [Tutorial: Sincronizar un panel de tareas personalizado con un botón de la cinta de opciones](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).  
  
-   Cree un panel de tareas personalizado para cada mensaje de correo electrónico que se abre en Outlook. Para obtener más información, consulta [Tutorial: Mostrar paneles de tareas personalizados con mensajes de correo electrónico en Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).  
  
## Vea también  
 [Paneles de tareas personalizados](../vsto/custom-task-panes.md)   
 [Cómo: Agregar un panel de tareas personalizado a una aplicación](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Tutorial: Sincronizar un panel de tareas personalizado con un botón de la cinta de opciones](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [Tutorial: Mostrar paneles de tareas personalizados con mensajes de correo electrónico en Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)  
  
  