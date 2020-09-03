---
title: 'Diseñador de flujo de trabajo: definir y consumir delegados de actividad'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 41271266793927f6029f50c0411bb9a150f5a64a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817507"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Definir y consumir delegados de actividad en el Diseñador de flujo de trabajo

.NET Framework 4,5 incluye un diseñador integrado para la <xref:System.Activities.Statements.InvokeDelegate> actividad. Este diseñador se puede usar para asignar delegados a la actividad que se derivan de <xref:System.Activities.ActivityDelegate>, como <xref:System.Activities.ActivityAction> o <xref:System.Activities.ActivityFunc%601>.

## <a name="define-an-activity-delegate"></a>Definir un delegado de actividad

1. Cree un nuevo proyecto de **aplicación de consola de flujos de trabajo** .

   > [!NOTE]
   > Si no ve las plantillas de proyecto de **flujo de trabajo** , instale primero el **Windows Workflow Foundation** componente de Visual Studio. Para obtener instrucciones detalladas, consulte [instalación de Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

3. Haga clic con el botón derecho en el proyecto en **Explorador de soluciones** y seleccione **Agregar**  >  **nuevo elemento**. Seleccione la categoría **flujo de trabajo** y, a continuación, seleccione la plantilla elemento de **actividad** . Asigne a la nueva actividad el nombre el **deforeach. Xaml** y, a continuación, seleccione **Aceptar**.

   La actividad se abre en el diseñador de flujo de trabajo.

4. En el Diseñador de flujo de trabajo, haga clic en la pestaña **argumentos** .

5. Haga clic en **Crear argumento**. Asigne un nombre a los nuevos **elementos**de argumento.

6. En la columna **tipo de argumento** , seleccione **matriz de [T]**.

7. En el explorador de tipos, seleccione **objeto** y, a continuación, haga clic en **Aceptar**.

8. Vuelva a hacer clic en **crear argumento** . Nombre el nuevo **cuerpo**del argumento. En la columna **Dirección** del nuevo argumento, seleccione **propiedad**.

9. En la columna tipo de argumento, seleccione **Buscar tipos** .

10. En el explorador de tipos, escriba **ActivityAction** en el campo **nombre de tipo** . Seleccione **ActivityAction \<T> ** en la vista de árbol. Seleccione **objeto** en la lista desplegable que aparece para asignar el tipo **ActivityAction \<Object> ** al argumento.

11. Arrastre una <xref:System.Activities.Statements.While> actividad desde la sección **flujo de control** del cuadro de herramientas hasta la superficie del diseñador.

12. Seleccione la <xref:System.Activities.Statements.While> actividad y seleccione la pestaña **variables** .

13. Seleccione **crear variable**. Asigne al nuevo **Índice**el nombre de la variable.

14. En la columna **tipo de variable** , seleccione **Int32**. Deje el **ámbito** como **While**y la columna **predeterminada** en blanco.

15. Establezca la propiedad **condición** de la <xref:System.Activities.Statements.While> actividad en **index < items. length;**.

16. Arrastre una <xref:System.Activities.Statements.InvokeDelegate> actividad desde la sección **primitivas** del cuadro de herramientas hasta el **cuerpo** de la <xref:System.Activities.Statements.While> actividad.

17. Seleccione **cuerpo** en la lista desplegable delegado.

18. En la cuadrícula de **propiedades** de la <xref:System.Activities.Statements.InvokeDelegate> actividad, haga clic en el botón **...** de la propiedad **argumentos delegados** .

19. En la columna **valor** del argumento denominado **argument**, escriba **Items [index]**. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **DelegateArguments** .

20. Arrastre una actividad <xref:System.Activities.Statements.Assign> sobre la línea horizontal bajo la actividad <xref:System.Activities.Statements.InvokeDelegate>. <xref:System.Activities.Statements.Assign>Se crea la actividad y <xref:System.Activities.Statements.Sequence> se crea automáticamente una actividad para que contenga las dos actividades en la sección de **cuerpo** de la actividad de la **instrucción sinforeach** . La secuencia es necesaria, ya que la sección de **cuerpo** solo puede contener una única actividad. La creación automática de una nueva <xref:System.Activities.Statements.Sequence> actividad es una característica nueva de .NET Framework 4,5.

21. Establezca la propiedad **to** de la <xref:System.Activities.Statements.Assign> actividad en **index**. Establezca la propiedad **Value** de la actividad **assign** en **index + 1**.

    La actividad @ **foreach** personalizada invoca una actividad arbitraria una vez por cada valor que se pasa a través de la colección de **elementos** , con los valores de la colección como entradas para la actividad.

## <a name="use-the-custom-activity-in-a-workflow"></a>Usar la actividad personalizada en un flujo de trabajo

1. Compile el proyecto presionando **Ctrl** + **MAYÚS** + **B**.

2. En **Explorador de soluciones**, Abra **Workflow1. Xaml** en el diseñador.

3. Arrastre una actividad @ **foreach** desde el cuadro de herramientas a la superficie del diseñador. La actividad está en una sección del cuadro de herramientas con el mismo nombre que el proyecto.

4. Establezca la propiedad **Items** de la actividad **sinforeach** en **nuevo objeto [] {1, "ABC"}**.

5. Arrastre una <xref:System.Activities.Statements.WriteLine> actividad de la sección **primitivas** del cuadro de herramientas a la sección **Delegate: Body** de la actividad **sinforeach** .

6. Establezca la propiedad **Text** de la <xref:System.Activities.Statements.WriteLine> actividad en **argument. ToString ()**.

Cuando se ejecuta el flujo de trabajo, la consola muestra el siguiente resultado:

**1** 
 **ABC**
