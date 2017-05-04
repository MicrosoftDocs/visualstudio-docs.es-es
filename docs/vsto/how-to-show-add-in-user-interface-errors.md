---
title: "C&#243;mo: Mostrar errores de la interfaz de usuario | Microsoft Docs"
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
  - "complementos (desarrollo de Office en Visual Studio), errores de interfaz de usuario"
  - "errores (desarrollo de Office en Visual Studio), errores de interfaz de usuario"
  - "interfaces de usuario [desarrollo de Office en Visual Studio], errores"
  - "complementos de nivel de aplicación (desarrollo de Office en Visual Studio), errores de interfaz de usuario"
ms.assetid: aa82cc04-e616-4501-940c-79d11fb393cc
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# C&#243;mo: Mostrar errores de la interfaz de usuario
  De forma predeterminada, si un complemento de VSTO intenta manipular la interfaz de usuario \(IU\) de Microsoft Office y no lo consigue, no se muestra ningún mensaje de error. Sin embargo, puede configurar las aplicaciones de Microsoft Office para mostrar los mensajes de errores relacionados con la interfaz de usuario. Puede usar estos mensajes para ayudar a determinar por qué no aparece una cinta personalizada, o por qué aparece una cinta pero ningún control.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### Cómo mostrar errores de la interfaz de usuario  
  
1.  Inicie la aplicación.  
  
2.  Haga clic en la pestaña **Archivo**.  
  
3.  Haga clic en **Opciones**.  
  
4.  En el panel de categorías, haga clic en **Opciones avanzadas**.  
  
5.  En el panel de detalles, seleccione **Mostrar errores de interfaz de usuario de complemento de VSTO** y luego haga clic en **Aceptar**.  
  
    > [!NOTE]  
    >  Para Outlook, la casilla **Mostrar errores de interfaz de usuario de complemento de VSTO** se encuentra en la sección **Desarrollador** del panel de detalles. Para otras aplicaciones, la casilla se encuentra en la sección **General** del panel de detalles.  
  
## Vea también  
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)   
 [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)  
  
  