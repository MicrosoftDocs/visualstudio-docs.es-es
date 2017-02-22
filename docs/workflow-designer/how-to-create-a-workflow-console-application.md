---
title: "Crear una aplicaci&#243;n de consola de flujos de trabajo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
caps.handback.revision: 16
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Crear una aplicaci&#243;n de consola de flujos de trabajo
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] le permite crear flujos de trabajo para ejecutar sistemas o procesos humanos.[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] proporciona la superficie de diseño para la creación de estos flujos de trabajo.El [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] se puede usar para crear flujos de trabajo desde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o se puede integrar en otras aplicaciones que hospedan en otro host el diseñador.  
  
 En este tema se describe cómo usar el [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] en [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] para crear un flujo de trabajo en una aplicación de consola.  
  
### Para crear una aplicación de consola de flujos de trabajo  
  
1.  Inicie [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  En el menú **Archivo**, elija **Nuevo** y después seleccione **Proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto**.  
  
3.  En el panel **Plantillas instalas**, seleccione **Flujo de trabajo** en las agrupaciones **Visual C\#** o **Visual Basic**, en función del lenguaje preferido.  
  
4.  En panel central, seleccione **Aplicación de consola de flujos de trabajo**.  
  
5.  En el cuadro **Nombre**, escriba un nombre descriptivo para que resulte sencillo identificar el proyecto.  
  
6.  En el cuadro **Ubicación**, escriba el directorio en el que desee guardar el proyecto o haga clic en **Examinar** para navegar hasta él.  
  
7.  En el cuadro **Solución**, escriba el nombre de la nueva solución.Haga clic en **Aceptar** para crear la aplicación.  
  
    > [!NOTE]
    >  Si desea agregar una aplicación de consola de flujos de trabajo a una solución existente, ábrala en [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], haga clic con el botón secundario en la solución en el **Explorador de soluciones**, seleccione **Agregar** y luego **Nuevo proyecto...** para abrir el cuadro de diálogo **Nuevo proyecto**.Continúe de la forma descrita anteriormente en este procedimiento.  
  
8.  La plantilla del proyecto crea una definición de flujo de trabajo en XAML y la definición de la aplicación de consola está en código fuente.El [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] se abre y muestra el lienzo para el flujo de trabajo que creó.  
  
9. Para crear un flujo de trabajo, arrastre actividades u otros elementos de flujo de trabajo desde el **Cuadro de herramientas** hasta la superficie de diseño del flujo de trabajo.  
  
## Vea también  
 [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)