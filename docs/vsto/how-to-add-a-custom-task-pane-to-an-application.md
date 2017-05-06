---
title: "C&#243;mo: Agregar un panel de tareas personalizado a una aplicaci&#243;n"
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
  - "paneles de tareas personalizados [desarrollo de Office en Visual Studio], agregar a aplicaciones"
  - "paneles de tareas [desarrollo de Office en Visual Studio], agregar a aplicaciones"
ms.assetid: 67b4ed5b-d77e-4630-b851-34bb25bdc9b3
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# C&#243;mo: Agregar un panel de tareas personalizado a una aplicaci&#243;n
  Puede agregar un panel de tareas personalizado a las aplicaciones enumeradas anteriormente mediante el complemento de VSTO.  Para obtener más información, consulte [Paneles de tareas personalizados](../vsto/custom-task-panes.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos.  Para obtener más información, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Agregar un panel de tareas personalizado a una aplicación  
  
#### Para agregar un panel de tareas personalizado a una aplicación  
  
1.  Abra o cree un proyecto de complemento de VSTO para una de las aplicaciones enumeradas anteriormente.  Para obtener más información, consulte [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  En el menú **Proyecto**, haga clic en **Agregar control de usuario**.  
  
3.  En el cuadro de diálogo **Agregar nuevo elemento**, cambie el nombre del control de usuario nuevo a **MyUserControl** y, a continuación, haga clic en **Agregar**.  
  
     Se abre el control de usuario en el diseñador.  
  
4.  Agregue uno o más controles de Windows Forms desde el **Cuadro de herramientas** al control de usuario.  
  
5.  Abra el archivo de código **ThisAddIn.cs** o **ThisAddIn.vb**.  
  
6.  Agregue el código siguiente a la clase `ThisAddIn`.  Este código declara instancias de `MyUserControl` y <xref:Microsoft.Office.Tools.CustomTaskPane> como miembros de la clase `ThisAddIn`.  
  
     [!code-csharp[Trin_TaskPaneBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/VB/ThisAddIn.vb#1)]  
  
7.  Agregue el código siguiente al controlador de eventos `ThisAddIn_Startup`.  Este código crea un nuevo <xref:Microsoft.Office.Tools.CustomTaskPane> agregando el objeto `MyUserControl` a la colección `CustomTaskPanes`.  El código también muestra el panel de tareas.  
  
     [!code-csharp[Trin_TaskPaneBasic#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneBasic#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/VB/ThisAddIn.vb#2)]  
  
    > [!NOTE]  
    >  Este código asocia el panel de tareas personalizado a la ventana activa de la aplicación.  En algunas aplicaciones, tal vez desee modificar este código para asegurarse de que el panel de tareas aparece con otros documentos o elementos de la aplicación.  Para obtener más información, consulte [Paneles de tareas personalizados](../vsto/custom-task-panes.md).  
  
## Vea también  
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Paneles de tareas personalizados](../vsto/custom-task-panes.md)   
 [Tutorial: Automatizar una aplicación desde un panel de tareas personalizado](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)  
  
  