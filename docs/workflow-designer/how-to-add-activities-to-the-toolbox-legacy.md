---
title: "C&#243;mo: Agregar actividades al cuadro de herramientas (Heredado) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "actividades, agregar al cuadro de herramientas"
  - "Cuadro de herramientas, agregar actividades"
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# C&#243;mo: Agregar actividades al cuadro de herramientas (Heredado)
Cuando se compila una solución de flujo de trabajo con [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado que tiene como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], se pueden agregar actividades personalizadas al proyecto de flujo de trabajo y a sus diseñadores colocados en el **Cuadro de herramientas** para facilitar el acceso.También puede agregar directamente al **Cuadro de herramientas** las actividades de una biblioteca de vínculos dinámicos \(DLL\).  
  
### Para agregar al cuadro de herramientas una actividad de una DLL  
  
1.  Haga clic con el botón secundario en la superficie de la ventana del cuadro de herramientas debajo de **Windows Workflow** y, a continuación, haga clic en **Elegir elementos**.  
  
2.  En el cuadro de diálogo **Elegir elementos del cuadro de herramientas**, haga clic en la pestaña **Componentes de System.Activities** y, a continuación, en **Examinar** desde el lado inferior derecho de la ventana.  
  
3.  Seleccione la DLL en el directorio de archivos que contiene la implementación de la actividad personalizada para agregar el **Cuadro de herramientas** y, a continuación, haga clic en **Abrir**.  
  
4.  Haga clic en **Aceptar** para finalizar de agregar la actividad al cuadro de herramientas.  
  
## Vea también  
 [Usar el diseñador de actividad Legacy](../workflow-designer/using-the-legacy-activity-designer.md)   
 [Actividades de flujo de trabajo heredadas](../workflow-designer/legacy-workflow-activities.md)