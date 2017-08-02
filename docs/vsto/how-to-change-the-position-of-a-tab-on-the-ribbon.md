---
title: "C&#243;mo: Cambiar la posici&#243;n de una pesta&#241;a en la cinta de opciones"
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
  - "Cinta [desarrollo de Office en Visual Studio], pestañas"
ms.assetid: 3f0906e3-9708-4136-ac49-986bc4c92ea4
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# C&#243;mo: Cambiar la posici&#243;n de una pesta&#241;a en la cinta de opciones
  Puede cambiar el orden de las pestañas personalizadas de una Cinta mediante el **Editor de la colección de pestañas**.  Puede colocar las pestañas personalizadas antes o después de una pestaña integrada en la Cinta.  Una ficha integrada es una ficha que ya está en la cinta de opciones de una aplicación de Microsoft Office.  Por ejemplo, la ficha **Datos** es una ficha integrada en Excel.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### Para cambiar el orden de las fichas en la cinta de opciones  
  
1.  Seleccione el archivo de código de la cinta de opciones \(archivo .vb o .cs\) en el **Explorador de soluciones**.  
  
2.  En el menú **Ver**, haga clic en **Diseñador**.  
  
3.  Haga clic con el botón secundario en el diseñador de la cinta de opciones y, a continuación, haga clic en **Propiedades**.  
  
4.  En la ventana **Propiedades**, seleccione la propiedad **Fichas** y, a continuación, haga clic en el botón de puntos suspensivos \(![Elipse del Diseñador de ASP.NET Mobile](~/docs/sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")\).  
  
     Aparecerá el **Editor de la colección de fichas**.  
  
5.  En el **Editor de la colección de fichas**, en la lista **Miembros**, seleccione la ficha que desea mover y haga clic en las flechas arriba o abajo para cambiar el orden de la ficha.  
  
### Para colocar una pestaña antes o después de una pestaña integrada en la Cinta  
  
1.  En el diseñador de la Cinta, seleccione una pestaña.  
  
2.  En la ventana **Propiedades** , expanda la propiedad **ControlId** , y se asegura de que el valor de la propiedad **ControlIdType** está establecido en **Personalizado**.  
  
3.  En la ventana **Propiedades**, expanda la propiedad **Posición**.  
  
4.  Establezca **PositionType** en el valor adecuado:  
  
    -   **BeforeOfficeId** coloca el grupo antes de una pestaña integrada especificada.  
  
    -   **AfterOfficeId** coloca el grupo después de una pestaña integrada especificada.  
  
5.  Establezca la propiedad **OfficeId** en el identificador de control de una pestaña integrada.  
  
     Para obtener una lista de id. de control, vea [Archivos de Ayuda de Office 2010: Identificadores de Control de la interfaz de usuario de Office Fluent](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## Vea también  
 [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)   
 [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)   
 [XML de la cinta de opciones](../vsto/ribbon-xml.md)   
 [Tutorial: Crear una pestaña personalizada usando el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Tutorial: Crear una pestaña personalizada usando XML de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  