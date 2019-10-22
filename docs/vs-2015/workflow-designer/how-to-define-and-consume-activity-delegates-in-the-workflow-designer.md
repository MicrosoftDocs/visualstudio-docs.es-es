---
title: 'Cómo: definir y utilizar delegados de actividad en el Diseñador de flujo de trabajo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 26ba92a2ba7aa6eed471383c875104549e896804
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603849"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Definir y consumir delegados de actividad en el Diseñador de flujo de trabajo
[!INCLUDE[net_v45](../includes/net-v45-md.md)] incluye un nuevo diseñador estándar para la actividad <xref:System.Activities.Statements.InvokeDelegate>. Este diseñador se puede usar para asignar delegados a la actividad que se derivan de <xref:System.Activities.ActivityDelegate>, como <xref:System.Activities.ActivityAction> o <xref:System.Activities.ActivityFunc%601>.

### <a name="define-an-activity-delegate"></a>Definir un delegado de actividad

1. En [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], seleccione **archivo**, **nuevo**, **proyecto**. Seleccione el nodo de **flujo de trabajo** de la izquierda y la plantilla de aplicación de consola de **flujos de trabajo** a la derecha. Asigne un nombre al proyecto (si lo desea) y haga clic en **Aceptar**.

2. Haga clic con el botón derecho en el proyecto en **Explorador de soluciones** y seleccione **Agregar**, **nuevo elemento.** ... Seleccione el nodo de **flujo de trabajo** a la izquierda y la plantilla de **actividad** de la derecha. Asigne a la nueva actividad el nombre, el **. Xaml** , y haga clic en **Aceptar**. La actividad se abrirá en el diseñador de flujo de trabajo.

3. En el diseñador de flujo de trabajo, haga clic en la pestaña **argumentos** .

4. Haga clic en **crear argumento**. Asigne un nombre a los nuevos **elementos**de argumento.

5. En la columna **tipo de argumento** , seleccione **matriz de [T]** .

6. En el explorador de tipos, seleccione **objeto**. Haga clic en **Aceptar**.

7. Vuelva a hacer clic en **crear argumento** . Nombre el nuevo **cuerpo**del argumento. En la columna **Dirección** del nuevo argumento, seleccione **propiedad**.

8. En la columna tipo de argumento, seleccione **Buscar tipos..** .

9. En el explorador de tipos, escriba **ActivityAction** en el campo **nombre de tipo** . Seleccione **ActivityAction \<T >** en la vista de árbol. Seleccione **objeto** en la lista desplegable que parece asignar el tipo **ActivityAction \<Object >** al argumento.

10. Arrastre una actividad <xref:System.Activities.Statements.While> desde la sección **flujo de control** del cuadro de herramientas hasta la superficie del diseñador.

11. Seleccione la actividad <xref:System.Activities.Statements.While> y seleccione la pestaña **variables** .

12. Seleccione **crear variable**. Asigne al nuevo **Índice**el nombre de la variable.

13. En la columna **tipo de variable** , seleccione **Int32**. Deje el **ámbito** como **While**y la columna **predeterminada** en blanco.

14. Establezca la propiedad **condición** de la actividad <xref:System.Activities.Statements.While> en **index < items. length;** .

15. Arrastre una actividad <xref:System.Activities.Statements.InvokeDelegate> desde la sección **primitivas** del cuadro de herramientas hasta el **cuerpo** de la actividad <xref:System.Activities.Statements.While>.

16. Seleccione **cuerpo** en la lista desplegable delegado.

17. En la cuadrícula de **propiedades** de la actividad <xref:System.Activities.Statements.InvokeDelegate>, haga clic en **...** en la propiedad **argumentos delegados** .

18. En la columna **valor** del argumento denominado **argument**, escriba **Items [index]** . Haga clic en **Aceptar** para cerrar el cuadro de diálogo **DelegateArguments** .

19. Arrastre una actividad <xref:System.Activities.Statements.Assign> sobre la línea horizontal bajo la actividad <xref:System.Activities.Statements.InvokeDelegate>. Se creará la actividad <xref:System.Activities.Statements.Assign> y se creará automáticamente una actividad <xref:System.Activities.Statements.Sequence> para contener las dos actividades en la sección **cuerpo** de la actividad **sinforeach** . La secuencia es necesaria, ya que la sección de **cuerpo** solo puede contener una única actividad. La creación automática de una nueva actividad <xref:System.Activities.Statements.Sequence> es una nueva característica de [!INCLUDE[net_v45](../includes/net-v45-md.md)].

20. Establezca la propiedad **to** de la actividad <xref:System.Activities.Statements.Assign> en **index**. Establezca la propiedad **Value** de la actividad **assign** en **index + 1**.

    La actividad @ **foreach** personalizada invocará ahora una actividad arbitraria una vez por cada valor que se le haya pasado a través de la colección de **elementos** , con los valores de la colección como entradas para la actividad.

### <a name="use-the-custom-activity-in-a-workflow"></a>Usar la actividad personalizada en un flujo de trabajo

1. Para compilar el proyecto, presione **Ctrl + Mayús + B**.

2. En **Explorador de soluciones**, Abra **Workflow1. Xaml** en el diseñador.

3. Arrastre una actividad @ **foreach** desde el cuadro de herramientas a la superficie del diseñador. La actividad estará en una sección del cuadro de herramientas con el mismo nombre que el proyecto.

4. Establezca la propiedad **Items** de la actividad **sinforeach** en **nuevo objeto [] {1, "ABC"}** .

5. Arrastre una actividad <xref:System.Activities.Statements.WriteLine> desde la sección **primitivas** del cuadro de herramientas hasta la sección **Delegate: Body** de la actividad @ **foreach** .

6. Establezca la propiedad **Text** de la actividad <xref:System.Activities.Statements.WriteLine> en **argument. ToString ()** .

   Cuando se ejecuta el flujo de trabajo, la consola mostrará lo siguiente:

   **1** 
   **ABC**