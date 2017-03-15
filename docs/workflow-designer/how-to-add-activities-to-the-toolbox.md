---
title: "Agregar actividades al cuadro de herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
caps.latest.revision: 16
caps.handback.revision: 16
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Agregar actividades al cuadro de herramientas
En su solución, se pueden agregar actividades al **Cuadro de herramientas** de varias maneras diferentes.Puede agregarlas desde dentro de su proyecto actual y hacer referencia a las misas desde un proyecto diferente o desde un ensamblado diferente.  
  
### Para agregar una actividad desde su proyecto actual  
  
1.  Agregue una nueva actividad personalizada al proyecto de flujo de trabajo actual.[!INCLUDE[crabout](../test/includes/crabout_md.md)] cómo agregar una nueva actividad personalizada al proyecto, vea [Cómo agregar un nuevo elemento a un proyecto de flujo de trabajo](../Topic/How%20to:%20Add%20a%20New%20Item%20to%20a%20Workflow%20Project.md).  
  
2.  Agregue lógica personalizada a su actividad.  
  
3.  Compile el proyecto.Si la compilación se efectúa correctamente, en el **Cuadro de herramientas** se muestra una nueva categoría denominada "\<*project name*\>" con la actividad personalizada incluida en esa categoría.  
  
    > [!NOTE]
    >  Si se restablece el cuadro de herramientas, las actividades personalizadas se quitarán, incluso si la solución se compila de nuevo.Para volver a rellenar el cuadro de herramientas con actividades personalizadas después de que se haya restablecido, reinicie [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
    > [!NOTE]
    >  El cuadro de herramientas solo puede mostrar una actividad de un nombre especificado.Si dos actividades de distintos ensamblados tienen el mismo nombre de clase, solo se mostrará una.  
  
    > [!NOTE]
    >  El dominio de aplicación se comparte entre las instancias del editor; si se usan variables estáticas, se compartirán entre las instancias del editor también.Si este no es el comportamiento deseado, se debe usar un servicio para hacer un seguimiento de las instancias variables.Vea [Utilizar el contexto de edición de ModelItem](../Topic/Using%20the%20ModelItem%20Editing%20Context.md) para obtener información sobre cómo usar servicios dentro del diseñador.  
  
### Para agregar una actividad desde un proyecto diferente  
  
1.  Abra una solución que contenga al menos un proyecto de flujo de trabajo y un proyecto de biblioteca de actividades personalizado u otro proyecto de flujo de trabajo que defina una actividad personalizada.  
  
2.  Compile ambos proyectos.Si las compilaciones se efectúan correctamente, en el **Cuadro de herramientas** se muestra una nueva categoría denominada "\<*project name*\>" con la actividad personalizada incluida en esa categoría.  
  
### Para agregar una actividad al cuadro de herramientas desde un ensamblado  
  
1.  Abra una solución de flujo de trabajo.  
  
2.  En el menú **Herramientas**, seleccione **Elegir elementos del cuadro de herramientas...**.  
  
3.  En el cuadro de diálogo **Elegir elementos del cuadro de herramientas**, seleccione la pestaña **Componentes de System.Activities**, a continuación, haga clic en **Examinar** para navegar hasta el ensamblado que contiene la actividad personalizada que desee agregar.  
  
4.  Seleccione el ensamblado y haga clic en **Aceptar**.El componente de actividad personalizado se agrega a la lista de componentes y se selecciona automáticamente.  
  
    1.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo.  
  
5.  Para mostrar el cuadro de herramientas, seleccione **Cuadro de herramientas** en el menú **Ver**.  
  
6.  La actividad personalizada aparece en el **Cuadro de herramientas** en la categoría que fue el foco antes de que se agregara el elemento.Por ejemplo, si la categoría **General** estuviera seleccionada en el **Cuadro de herramientas**, antes de agregar el elemento del cuadro de herramientas, la actividad aparece en la categoría **General**.  
  
## Vea también  
 [Utilizar el Diseñador de flujo de trabajo](../workflow-designer/using-the-workflow-designer.md)