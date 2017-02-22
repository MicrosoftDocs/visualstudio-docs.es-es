---
title: "C&#243;mo: Crear aplicaciones de consola de flujos de trabajo secuenciales (Heredado) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "aplicaciones de consola, flujo de trabajo secuencial"
  - "flujos de trabajo secuenciales, aplicaciones de consola"
  - "flujos de trabajo, aplicaciones de consola"
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# C&#243;mo: Crear aplicaciones de consola de flujos de trabajo secuenciales (Heredado)
Siga estos pasos para crear un proyecto de aplicación de consola de flujos de trabajo secuenciales mediante el uso de [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] heredado proporcionado por [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].Use el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### Para crear una aplicación de consola de flujos de trabajo secuenciales  
  
1.  Inicie Visual Studio.  
  
2.  En el menú **Archivo**, elija **Nuevo** y después seleccione **Proyecto**.  
  
     Se abre el cuadro de diálogo **Nuevo proyecto**.  
  
3.  Seleccione la opción **.NET Framework 3.0** o la opción **.NET Framework 3.5** en la lista desplegable situada en la parte superior de la ventana **Nuevo proyecto** para tener acceso al diseñador heredado.  
  
    > [!NOTE]
    >  La opción predeterminada de [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] es **.NET Framework 4**.Esta opción se usa para crear aplicaciones [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] que tienen como destino [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] y no usa el diseñador heredado.  
  
4.  En el panel **Tipos de proyecto**, seleccione proyectos de Visual C\# o proyectos de Visual Basic \(en **Otros lenguajes**\) y, a continuación, seleccione **Flujo de trabajo**.  
  
5.  En el panel **Plantillas**, seleccione **Aplicación de consola de flujos de trabajo secuenciales**.  
  
6.  En el cuadro **Nombre**, escriba un nombre descriptivo para que resulte sencillo identificar el proyecto.  
  
7.  En el cuadro **Ubicación**, escriba el directorio donde desea guardar el proyecto o haga clic en el botón **Examinar** para navegar hasta él.  
  
     Se abrirá el Diseñador de Windows Forms, que mostrará el formulario Form1 del proyecto creado.  
  
8.  Haga clic en **Aceptar**.  
  
     Se abre el Diseñador de flujo de trabajo y muestra la superficie de diseño de flujo de trabajo del flujo de trabajo secuencial que ha creado.  
  
9. Arrastre una actividad del **Cuadro de herramientas** a la superficie de diseño del área **Colocar actividad**.  
  
## Vea también  
 [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Developing Workflows](http://msdn.microsoft.com/es-es/557bcb1f-a7ab-49f6-8df7-2706b7001301)