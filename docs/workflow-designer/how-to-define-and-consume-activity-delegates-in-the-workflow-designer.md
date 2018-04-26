---
title: 'Diseñador de flujo de trabajo: Cómo: definir y utilizar delegados de actividad'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 73bf61c845b0124a8350f61c161ded1cf0c80043
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Definir y consumir delegados de actividad en el Diseñador de flujo de trabajo

.NET framework 4.5 incluye un nuevo diseñador de out-of-box para la <xref:System.Activities.Statements.InvokeDelegate> actividad. Este diseñador se puede usar para asignar delegados a la actividad que se derivan de <xref:System.Activities.ActivityDelegate>, como <xref:System.Activities.ActivityAction> o <xref:System.Activities.ActivityFunc%601>.

## <a name="define-an-activity-delegate"></a>Definir un delegado de actividad

1.  En Visual Studio, seleccione **archivo**, **New**, **proyecto**. Seleccione el **flujo de trabajo** nodo a la izquierda y la **aplicación de consola de flujos de trabajo** plantilla a la derecha. Denomine el proyecto (si lo desea) y haga clic en **Aceptar**.

2.  Haga doble clic en el proyecto en **el Explorador de soluciones** y seleccione **agregar**, **nuevo elemento...** . Seleccione el **flujo de trabajo** nodo a la izquierda y la **actividad** plantilla a la derecha. Nombre de la nueva actividad **MyForEach.xaml** y haga clic en **Aceptar**. La actividad se abrirá en el diseñador de flujo de trabajo.

3.  En el Diseñador de flujo de trabajo, haga clic en el **argumentos** ficha.

4.  Haga clic en **crear argumento**. Nombre del nuevo argumento **elementos**.

5.  En el **tipo de argumento** columna, seleccione **matriz de [T]**.

6.  En el Explorador de tipo, seleccione **objeto**. Click **Ok**.

7.  Haga clic en **crear argumento** nuevo. Nombre del nuevo argumento **cuerpo**. En el **dirección** columna para el nuevo argumento, seleccione **propiedad**.

8.  En la columna de tipo de argumento, seleccione **buscar tipos...**

9. En el explorador, escriba **ActivityAction** en el **nombre de tipo** campo. Seleccione **ActivityAction\<T >** en la vista de árbol. Seleccione **objeto** en la lista desplegable que aparece para asignar el tipo **ActivityAction\<objeto >** al argumento.

10. Arrastre un <xref:System.Activities.Statements.While> actividad desde la **flujo de Control** sección del cuadro de herramientas a la superficie del diseñador.

11. Seleccione el <xref:System.Activities.Statements.While> actividad y seleccione el **Variables** ficha.

12. Seleccione **crear Variable**. Nombre de la nueva variable **índice**.

13. En el **tipo de Variable** columna, seleccione **Int32**. Deje el **ámbito** como **mientras**y el **predeterminado** columna en blanco.

14. Establecer el **condición** propiedad de la <xref:System.Activities.Statements.While> actividad **índice < Items.Length;**.

15. Arrastre un <xref:System.Activities.Statements.InvokeDelegate> actividad desde la **primitivas** sección del cuadro de herramientas el **cuerpo** de la <xref:System.Activities.Statements.While> actividad.

16. Seleccione **cuerpo** en la lista desplegable de delegado.

17. En el **propiedades** cuadrícula para la <xref:System.Activities.Statements.InvokeDelegate> actividad, haga clic en el **...**  botón en el **argumentos de delegado** propiedad.

18. En el **valor** columna del argumento denominado **argumento**, escriba **elementos [índice]**. Haga clic en **Aceptar** para cerrar el **DelegateArguments** cuadro de diálogo.

19. Arrastre una actividad <xref:System.Activities.Statements.Assign> sobre la línea horizontal bajo la actividad <xref:System.Activities.Statements.InvokeDelegate>. El <xref:System.Activities.Statements.Assign> se creará la actividad y un <xref:System.Activities.Statements.Sequence> actividad se creará automáticamente para que contenga las dos actividades en el **cuerpo** sección de la **MyForEach** actividad. La secuencia es necesaria porque el **cuerpo** sección sólo puede contener una única actividad. Creación automática de un nuevo <xref:System.Activities.Statements.Sequence> actividad es una nueva característica de .NET Framework 4.5.

20. Establecer el **a** propiedad de la <xref:System.Activities.Statements.Assign> actividad **índice**. Establecer el **valor** propiedad de la **asignar** actividad para **index+1**.

 Personalizado **MyForEach** actividad ahora invocará una actividad arbitraria una vez por cada valor pasado en ella mediante la **elementos** colección, con los valores de la colección como entradas para la actividad.

## <a name="use-the-custom-activity-in-a-workflow"></a>Usar la actividad personalizada en un flujo de trabajo

1.  Compile el proyecto presionando **Ctrl + Mayús + B**.

2.  En **el Explorador de soluciones**, abra **Workflow1.xaml** en el diseñador.

3.  Arrastre un **MyForEach** actividad en el cuadro de herramientas a la superficie del diseñador. La actividad estará en una sección del cuadro de herramientas con el mismo nombre que el proyecto.

4.  Establecer el **elementos** propiedad de la **MyForEach** actividad **new Object [] {1, "abc"}**.

5.  Arrastre un <xref:System.Activities.Statements.WriteLine> actividad desde la **primitivas** sección del cuadro de herramientas el **Delegate: cuerpo** sección de la **MyForEach** actividad.

6.  Establecer el **texto** propiedad de la <xref:System.Activities.Statements.WriteLine> actividad **Argument.ToString ()**.

Cuando se ejecuta el flujo de trabajo, la consola muestra lo siguiente:

**1**
**abc**