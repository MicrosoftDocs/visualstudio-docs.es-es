---
title: "Crear una biblioteca de actividades | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
caps.handback.revision: 12
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Crear una biblioteca de actividades
Las actividades personalizadas se usan para modelar los procesos de negocio concretos de un flujo de trabajo.La plantilla Biblioteca de actividad de [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] se ha proporcionado para que pueda crear tales actividades personalizadas visualmente mediante el uso de [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
### Para crear una biblioteca de actividades de flujo de trabajo  
  
1.  Inicie [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  En el menú **Archivo**, elija **Nuevo** y después seleccione **Proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto**.  
  
3.  En el panel **Tipos de proyecto**, seleccione **Flujo de trabajo** en los proyectos **Visual C\#** o en las agrupaciones **Visual Basic** en función del lenguaje preferido.  
  
4.  En el panel **Plantillas**, seleccione **Biblioteca de actividades**.  
  
5.  En el cuadro **Nombre**, escriba un nombre descriptivo para facilitar la identificación del proyecto.  
  
6.  En el cuadro **Ubicación**, escriba el directorio en el que desee guardar el proyecto o haga clic en **Examinar** para navegar a él.  
  
7.  En el cuadro **Solución**, escriba un nombre descriptivo para la solución y haga clic en **Aceptar**.  
  
    > [!NOTE]
    >  Si desea agregar una aplicación de consola de flujos de trabajo a una solución existente, ábrala en [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], haga clic con el botón secundario en la solución en el **Explorador de soluciones**, seleccione **Agregar** y luego **Nuevo proyecto...** para abrir el cuadro de diálogo **Nuevo proyecto**.Continúe de la forma descrita anteriormente en este procedimiento.  
  
8.  La plantilla de proyecto crea una definición de actividad en XAML.[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] se abre y muestra el lienzo para su actividad personalizada.  
  
9. Arrastre una actividad desde el **Cuadro de herramientas** hasta la superficie de diseño para incluirla en la actividad personalizada.  
  
    > [!CAUTION]
    >  Solo puede tener una actividad secundaria en el cuerpo de la actividad personalizada; sin embargo, esa actividad de elemento secundario podría ser una actividad compuesta, como una actividad <xref:System.Activities.Statements.Sequence> o una actividad <xref:System.Activities.Statements.Flowchart>.  
  
## Vea también  
 [Cómo: Crear una actividad](../Topic/How%20to:%20Create%20an%20Activity.md)   
 [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)