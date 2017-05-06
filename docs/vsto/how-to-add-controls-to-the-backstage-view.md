---
title: "C&#243;mo: Agregar controles en la vista Backstage"
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
  - "controles, cinta de opciones"
  - "Cinta de opciones personalizada, menús"
  - "personalizar la cinta de opciones, menús"
  - "menús, personalizar"
  - "botón Microsoft Office"
  - "menú de Microsoft Office"
  - "Botón de Office"
  - "cinta de opciones, personalizar"
  - "cinta de opciones, menús"
ms.assetid: 4fda1278-9aea-4d54-928a-269a81584494
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# C&#243;mo: Agregar controles en la vista Backstage
  Puede utilizar el diseñador de la cinta de opciones para agregar controles al menú que se abre al hacer clic en la pestaña **Archivo** .  al ejecutar la aplicación, los controles que se agregan a **Archivo** la pestaña aparecen un grupo denominado **Complementos**.  
  
 No puede colocar controles antes o después de los controles integrados con el diseñador de la cinta en Visual Studio.  Un control compuesto es un control que aparece ya en la vista Backstage.  Si desea colocar controles antes o después de los controles integrados, debe utilizar Cinta XML.  Para obtener más información sobre **Cinta \(XML\)**, vea [XML de la cinta de opciones](../vsto/ribbon-xml.md).  Para obtener más información sobre cómo personalizar la vista Backstage, vea [Introduction to the Office 2010 Backstage View for Developers](http://go.microsoft.com/fwlink/?LinkId=182189) y [Customizing the Office 2010 Backstage View for Developers](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### Para agregar controles a la vista Backstage  
  
1.  Abra el elemento Cinta en la vista Diseño.  
  
     Para obtener información sobre cómo agregar un elemento **Cinta \(diseñador visual\)** al proyecto, vea [Cómo: Iniciarse en la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  En la cinta de opciones, haga clic en la pestaña **Archivo** .  
  
     Aparece un diseñador de menús.  Esta superficie de diseño no contiene ningún control.  
  
3.  Desde la ficha **Controles de la cinta de opciones de Office** del **Cuadro de herramientas**, arrastre cualquiera de los controles siguientes al diseñador de menús:  
  
    -   Button  
  
    -   CheckBox  
  
    -   Gallery  
  
    -   Menu  
  
    -   Separator  
  
    -   SplitButton  
  
    -   ToggleButton  
  
4.  Arrastre controles para moverlos a nuevas posiciones en el menú.  
  
## Vea también  
 [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)   
 [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)   
 [XML de la cinta de opciones](../vsto/ribbon-xml.md)   
 [Cómo: Iniciarse en la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Tutorial: Crear una pestaña personalizada usando el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  