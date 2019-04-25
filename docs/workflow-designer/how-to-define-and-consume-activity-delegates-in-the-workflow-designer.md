---
title: 'Diseñador de flujo de trabajo - Cómo: Definir y consumir a delegados de actividad'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c455f36d17b761fe02b7d78e96fbf2c4582d490d
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2019
ms.locfileid: "58415816"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Filtrar Definir y usar delegados de actividad en el Diseñador de flujo de trabajo

.NET framework 4.5 incluye un diseñador de out-of-box para el <xref:System.Activities.Statements.InvokeDelegate> actividad. Este diseñador se puede usar para asignar delegados a la actividad que se derivan de <xref:System.Activities.ActivityDelegate>, como <xref:System.Activities.ActivityAction> o <xref:System.Activities.ActivityFunc%601>.

## <a name="define-an-activity-delegate"></a>Definir un delegado de actividad

1. Cree un nuevo **aplicación de consola de flujos de trabajo** proyecto.

   > [!NOTE]
   > Si no ve el **flujo de trabajo** plantillas de proyecto, instale primero el **Windows Workflow Foundation** componente de Visual Studio. Para obtener instrucciones detalladas, consulte [instalar Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

3. Haga doble clic en el proyecto en **el Explorador de soluciones** y seleccione **agregar** > **nuevo elemento**. Seleccione el **flujo de trabajo** categoría y, a continuación, seleccione el **actividad** plantilla de elemento. Nombre de la nueva actividad **MyForEach.xaml** y, a continuación, seleccione **Aceptar**.

   La actividad se abre en el Diseñador de flujo de trabajo.

4. En el Diseñador de flujo de trabajo, haga clic en el **argumentos** ficha.

5. Haga clic en **crear argumento**. Asigne nombre al nuevo argumento **elementos**.

6. En el **tipo de argumento** columna, seleccione **matriz de [T]**.

7. En el Explorador de tipos, seleccione **objeto** y, a continuación, seleccione **Aceptar**.

8. Haga clic en **crear argumento** nuevo. Asigne nombre al nuevo argumento **cuerpo**. En el **dirección** columna para el argumento nuevo, seleccione **propiedad**.

9. En la columna de tipo de argumento, seleccione **buscar tipos**

10. En el explorador, escriba **ActivityAction** en el **nombre de tipo** campo. Seleccione **ActivityAction\<T >** en la vista de árbol. Seleccione **objeto** en la lista desplegable que aparece para asignar el tipo **ActivityAction\<objeto >** al argumento.

11. Arrastre un <xref:System.Activities.Statements.While> actividad desde la **flujo de Control** sección del cuadro de herramientas a la superficie del diseñador.

12. Seleccione el <xref:System.Activities.Statements.While> actividad y seleccione el **Variables** ficha.

13. Seleccione **crear Variable**. Nombre de la nueva variable **índice**.

14. En el **tipo de Variable** columna, seleccione **Int32**. Deje el **ámbito** como **mientras**y el **predeterminado** columna en blanco.

15. Establecer el **condición** propiedad de la <xref:System.Activities.Statements.While> actividad **índice < Items.Length;**.

16. Arrastre un <xref:System.Activities.Statements.InvokeDelegate> actividad desde el **primitivas** sección del cuadro de herramientas para el **cuerpo** de la <xref:System.Activities.Statements.While> actividad.

17. Seleccione **cuerpo** en la lista desplegable de delegado.

18. En el **propiedades** cuadrícula para el <xref:System.Activities.Statements.InvokeDelegate> actividad, haga clic en el **...**  situado en la **argumentos de delegado** propiedad.

19. En el **valor** columna del argumento denominado **argumento**, escriba **elementos [índice]**. Haga clic en **Aceptar** para cerrar el **DelegateArguments** cuadro de diálogo.

20. Arrastre una actividad <xref:System.Activities.Statements.Assign> sobre la línea horizontal bajo la actividad <xref:System.Activities.Statements.InvokeDelegate>. El <xref:System.Activities.Statements.Assign> se crea una actividad y un <xref:System.Activities.Statements.Sequence> actividad se crea automáticamente para contener las dos actividades en el **cuerpo** sección de la **MyForEach** actividad. La secuencia es necesaria porque el **cuerpo** sección solo puede contener una sola actividad. Creación automática de un nuevo <xref:System.Activities.Statements.Sequence> actividad es una característica nueva de .NET Framework 4.5.

21. Establecer el **a** propiedad de la <xref:System.Activities.Statements.Assign> actividad **índice**. Establecer el **valor** propiedad de la **asignar** actividad **index+1**.

    Personalizado **MyForEach** actividad invoca una actividad arbitraria una vez para cada valor pasado en ella mediante la **elementos** colección, con los valores de la colección como entradas para la actividad.

## <a name="use-the-custom-activity-in-a-workflow"></a>Usar la actividad personalizada en un flujo de trabajo

1.  Compile el proyecto presionando **Ctrl**+**MAYÚS**+**B**.

2.  En **el Explorador de soluciones**, abra **Workflow1.xaml** en el diseñador.

3.  Arrastre un **MyForEach** actividad desde el cuadro de herramientas a la superficie del diseñador. La actividad está en una sección del cuadro de herramientas con el mismo nombre que el proyecto.

4.  Establecer el **elementos** propiedad de la **MyForEach** actividad **new Object [] {1, "abc"}**.

5.  Arrastre un <xref:System.Activities.Statements.WriteLine> actividad desde la **primitivas** sección del cuadro de herramientas para el **Delegate: cuerpo** sección de la **MyForEach** actividad.

6.  Establecer el **texto** propiedad de la <xref:System.Activities.Statements.WriteLine> actividad **Argument.ToString ()**.

Cuando se ejecuta el flujo de trabajo, la consola muestra el siguiente resultado:

**1**
**abc**