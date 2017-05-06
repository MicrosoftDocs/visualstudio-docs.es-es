---
title: "C&#243;mo: Agregar un selector de cuadro de di&#225;logo a un grupo de la cinta de opciones"
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
  - "selector de cuadro de diálogo [desarrollo de Office en Visual Studio]"
  - "Cinta [desarrollo de Office en Visual Studio], selector de cuadro de diálogo"
ms.assetid: 5972664f-4e37-4dc6-90d0-69cedd057e60
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# C&#243;mo: Agregar un selector de cuadro de di&#225;logo a un grupo de la cinta de opciones
  Puede agregar un selector de cuadro de diálogo a cualquier grupo de una cinta de opciones.  Un selector del cuadro de diálogo es un icono pequeño que aparece en un grupo.  Los usuarios hacen clic en este icono para abrir cuadros de diálogo o paneles de tareas relacionados que proporcionen más opciones relacionadas con el grupo.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### Para agregar un selector de cuadro de diálogo a un grupo de la cinta de opciones  
  
1.  Seleccione el archivo de código de la cinta de opciones \(archivo .vb o .cs\) en el **Explorador de soluciones**.  
  
2.  En el menú **Ver**, haga clic en **Diseñador**.  
  
3.  En el diseñador de la cinta de opciones, haga clic con el botón secundario en cualquier grupo y, a continuación, haga clic en **Selector del cuadro de diálogo Agregar**.  
  
     Agregue código al evento <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> del grupo para abrir un cuadro de diálogo personalizado o integrado.  
  
## Vea también  
 [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)   
 [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)   
 [Información general sobre el modelo de objetos para la cinta de opciones](../vsto/ribbon-object-model-overview.md)   
 [XML de la cinta de opciones](../vsto/ribbon-xml.md)   
 [Cómo: Exportar una cinta de opciones del diseñador de la cinta de opciones a XML de la cinta de opciones](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Cómo: Cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)   
 [Cómo: Agregar controles en la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Personalizar una cinta de opciones para Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Cómo: Iniciarse en la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Cómo: Mostrar errores de la interfaz de usuario](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Tutorial: Crear una pestaña personalizada usando el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Tutorial: Actualizar los controles de una cinta de opciones en tiempo de ejecución](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Tutorial: Crear una pestaña personalizada usando XML de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  