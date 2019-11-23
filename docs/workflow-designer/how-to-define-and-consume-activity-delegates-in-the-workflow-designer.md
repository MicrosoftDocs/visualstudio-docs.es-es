---
title: 'Diseñador de flujo de trabajo: definir y consumir delegados de actividad'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 67e862e3772b157c4a0999ccd44c3698119ae8a8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650338"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Definir y consumir delegados de actividad en el Diseñador de flujo de trabajo

.NET Framework 4,5 incluye un diseñador integrado para la actividad <xref:System.Activities.Statements.InvokeDelegate>. Este diseñador se puede usar para asignar delegados a la actividad que se derivan de <xref:System.Activities.ActivityDelegate>, como <xref:System.Activities.ActivityAction> o <xref:System.Activities.ActivityFunc%601>.

## <a name="define-an-activity-delegate"></a>Definir un delegado de actividad

1. Cree un nuevo proyecto de **aplicación de consola de flujos de trabajo** .

   > [!NOTE]
   > Si no ve las plantillas de proyecto de **flujo de trabajo** , instale primero el **Windows Workflow Foundation** componente de Visual Studio. Para obtener instrucciones detalladas, consulte [instalación de Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

3. Haga clic con el botón derecho en el proyecto en **Explorador de soluciones** y seleccione **Agregar** > **nuevo elemento**. Seleccione la categoría **flujo de trabajo** y, a continuación, seleccione la plantilla elemento de **actividad** . Asigne a la nueva actividad el nombre el **deforeach. Xaml** y, a continuación, seleccione **Aceptar**.

   La actividad se abre en el diseñador de flujo de trabajo.

4. En el Diseñador de flujo de trabajo, haga clic en la pestaña **argumentos** .

5. Haga clic en **Crear argumento**. Asigne un nombre a los nuevos **elementos**de argumento.

6. En la columna **tipo de argumento** , seleccione **matriz de [T]** .

7. En el explorador de tipos, seleccione **objeto** y, a continuación, haga clic en **Aceptar**.

8. Vuelva a hacer clic en **crear argumento** . Nombre el nuevo **cuerpo**del argumento. En la columna **Dirección** del nuevo argumento, seleccione **propiedad**.

9. En la columna tipo de argumento, seleccione **Buscar tipos** .

10. En el explorador de tipos, escriba **ActivityAction** en el campo **nombre de tipo** . Seleccione **ActivityAction\<t >** en la vista de árbol. Seleccione **objeto** en la lista desplegable que parece asignar el tipo **ActivityAction\<objeto >** al argumento.

11. Arrastre una actividad <xref:System.Activities.Statements.While> desde la sección **flujo de control** del cuadro de herramientas hasta la superficie del diseñador.

12. Seleccione la actividad <xref:System.Activities.Statements.While> y seleccione la pestaña **variables** .

13. Seleccione **crear variable**. Asigne al nuevo **Índice**el nombre de la variable.

14. En la columna **tipo de variable** , seleccione **Int32**. Deje el **ámbito** como **While**y la columna **predeterminada** en blanco.

15. Establezca la propiedad **condición** de la actividad <xref:System.Activities.Statements.While> en **index < items. length;** .

16. Arrastre una actividad <xref:System.Activities.Statements.InvokeDelegate> desde la sección **primitivas** del cuadro de herramientas hasta el **cuerpo** de la actividad <xref:System.Activities.Statements.While>.

17. Seleccione **cuerpo** en la lista desplegable delegado.

18. En la cuadrícula de **propiedades** de la actividad <xref:System.Activities.Statements.InvokeDelegate>, haga clic en el botón **...** de la propiedad **argumentos delegados** .

19. En la columna **valor** del argumento denominado **argument**, escriba **Items [index]** . Haga clic en **Aceptar** para cerrar el cuadro de diálogo **DelegateArguments** .

20. Arrastre una actividad <xref:System.Activities.Statements.Assign> sobre la línea horizontal bajo la actividad <xref:System.Activities.Statements.InvokeDelegate>. Se crea la actividad <xref:System.Activities.Statements.Assign> y se crea automáticamente una actividad <xref:System.Activities.Statements.Sequence> para que contenga las dos actividades en la sección **cuerpo** de la actividad **sinforeach** . La secuencia es necesaria, ya que la sección de **cuerpo** solo puede contener una única actividad. La creación automática de una nueva actividad <xref:System.Activities.Statements.Sequence> es una característica nueva de .NET Framework 4,5.

21. Establezca la propiedad **to** de la actividad <xref:System.Activities.Statements.Assign> en **index**. Establezca la propiedad **Value** de la actividad **assign** en **index + 1**.

    La actividad @ **foreach** personalizada invoca una actividad arbitraria una vez por cada valor que se pasa a través de la colección de **elementos** , con los valores de la colección como entradas para la actividad.

## <a name="use-the-custom-activity-in-a-workflow"></a>Usar la actividad personalizada en un flujo de trabajo

1. Compile el proyecto presionando **Ctrl**+**MAYÚS**+**B**.

2. En **Explorador de soluciones**, Abra **Workflow1. Xaml** en el diseñador.

3. Arrastre una actividad @ **foreach** desde el cuadro de herramientas a la superficie del diseñador. La actividad está en una sección del cuadro de herramientas con el mismo nombre que el proyecto.

4. Establezca la propiedad **Items** de la actividad **sinforeach** en **nuevo objeto [] {1, "ABC"}** .

5. Arrastre una actividad <xref:System.Activities.Statements.WriteLine> desde la sección **primitivas** del cuadro de herramientas hasta la sección **Delegate: Body** de la actividad @ **foreach** .

6. Establezca la propiedad **Text** de la actividad <xref:System.Activities.Statements.WriteLine> en **argument. ToString ()** .

Cuando se ejecuta el flujo de trabajo, la consola muestra el siguiente resultado:

**1**
**abc**