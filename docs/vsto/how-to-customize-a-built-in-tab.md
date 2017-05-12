---
title: "C&#243;mo: Personalizar una pesta&#241;a integrada"
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
  - "pestañas integradas [desarrollo de Office en Visual Studio]"
  - "Cinta [desarrollo de Office en Visual Studio], pestañas"
ms.assetid: 197a7aaa-a51d-496c-b904-b9421849fad9
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# C&#243;mo: Personalizar una pesta&#241;a integrada
  Puede agregar grupos y controles a una pestaña integrada.  Una pestaña integrada es una pestaña que ya existe en la cinta de una aplicación de Microsoft Office.  Por ejemplo, la pestaña **Datos** es una pestaña integrada en Excel.  Al crear un grupo personalizado, este aparece al final de la pestaña, pero puede colocarlo en la parte que quiera de la pestaña.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  Puede agregar grupos a una pestaña integrada, pero no puede quitar grupos integrados de una pestaña integrada.  
  
### Para agregar grupos a una pestaña integrada  
  
1.  En el **Explorador de soluciones**, haga clic con el botón derecho en el archivo de código de la cinta y, a continuación, haga clic en **Ver diseñador**.  
  
    > [!NOTE]  
    >  Si no aparece el archivo de código de la cinta en el **Explorador de soluciones**, debe agregar un **elemento de Cinta** al proyecto.  Consulte [Cómo: Iniciarse en la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Haga clic con el botón derecho en cualquier pestaña del diseñador de la cinta y, a continuación, haga clic en **Propiedades**.  
  
3.  En la ventana **Propiedades**, expanda la propiedad **ControlId** y, a continuación, establezca la propiedad **ControlIdType** en **Office**.  
  
4.  Establezca la propiedad **OfficeId** en el *identificador de control* de la pestaña integrada que desee personalizar.  
  
     El identificador de control es el nombre que identifica de forma única a las fichas, grupos y controles que se integran en las aplicaciones de Microsoft Office.  
  
     Para ver una lista de identificadores de control, consulte [Archivos de ayuda de Office 2010: Identificadores de control de la interfaz de usuario de Office Fluent](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
5.  En la pestaña **Controles de la cinta de Office** del **Cuadro de herramientas**, arrastre los grupos hasta colocarlos sobre la pestaña.  
  
    > [!NOTE]  
    >  Los grupos integrados no aparecen en el diseñador.  Por lo tanto, la única manera de determinar si se está trabajando con una pestaña integrada consiste en examinar la propiedad **ControlId** de la pestaña.  
  
### Para colocar grupos en una pestaña integrada  
  
1.  En el diseñador de la cinta, seleccione un grupo personalizado.  
  
2.  En la ventana **Propiedades**, expanda la propiedad **Position**.  
  
3.  Establezca un valor adecuado para la propiedad **PositionType**.  
  
    -   **BeforeOfficeId** coloca el grupo antes de un grupo integrado especificado.  
  
    -   **AfterOfficeId** coloca el grupo después de un grupo integrado especificado.  
  
4.  Establezca la propiedad **OfficeId** en el identificador de control de un grupo integrado.  
  
     Para ver una lista de identificadores de control, consulte [Archivos de ayuda de Office 2010: Identificadores de control de la interfaz de usuario de Office Fluent](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## Vea también  
 [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)   
 [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)   
 [XML de la cinta de opciones](../vsto/ribbon-xml.md)   
 [Tutorial: Crear una pestaña personalizada usando el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Tutorial: Crear una pestaña personalizada usando XML de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Cómo: Iniciarse en la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Cómo: Cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Cómo: Agregar controles en la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Cómo: Mostrar errores de la interfaz de usuario](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  