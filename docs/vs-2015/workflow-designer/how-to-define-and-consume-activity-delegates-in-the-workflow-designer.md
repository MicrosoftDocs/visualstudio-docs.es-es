---
title: 'Cómo: definir y consumir delegados de actividad en el Diseñador de flujo de trabajo | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 5bf6a53879e90dab2a0a57d99ee27d81bd1dfc35
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582686"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Definir y consumir delegados de actividad en el Diseñador de flujo de trabajo
[!INCLUDE[net_v45](../includes/net-v45-md.md)] incluye un nuevo diseñador estándar para la actividad <xref:System.Activities.Statements.InvokeDelegate>. Este diseñador se puede usar para asignar delegados a la actividad que se derivan de <xref:System.Activities.ActivityDelegate>, como <xref:System.Activities.ActivityAction> o <xref:System.Activities.ActivityFunc%601>.  
  
### <a name="define-an-activity-delegate"></a>Definir un delegado de actividad  
  
1.  En [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], seleccione **archivo**, **New**, **proyecto**. Seleccione el **flujo de trabajo** nodo a la izquierda y el **aplicación de consola de flujos de trabajo** plantilla a la derecha. Denomine el proyecto (si lo desea) y haga clic en **Aceptar**.  
  
2.  Haga doble clic en el proyecto en **el Explorador de soluciones** y seleccione **agregar**, **nuevo elemento...** . Seleccione el **flujo de trabajo** nodo a la izquierda y el **actividad** plantilla a la derecha. Nombre de la nueva actividad **MyForEach.xaml** y haga clic en **Aceptar**. La actividad se abrirá en el diseñador de flujo de trabajo.  
  
3.  En el Diseñador de flujo de trabajo, haga clic en el **argumentos** ficha.  
  
4.  Haga clic en **crear argumento**. Asigne nombre al nuevo argumento **elementos**.  
  
5.  En el **tipo de argumento** columna, seleccione **matriz de [T]**.  
  
6.  En el Explorador de tipos, seleccione **objeto**. Haga clic en **Aceptar**.  
  
7.  Haga clic en **crear argumento** nuevo. Asigne nombre al nuevo argumento **cuerpo**. En el **dirección** columna para el argumento nuevo, seleccione **propiedad**.  
  
8.  En la columna de tipo de argumento, seleccione **buscar tipos...**  
  
9. En el explorador, escriba **ActivityAction** en el **nombre de tipo** campo. Seleccione **ActivityAction\<T >** en la vista de árbol. Seleccione **objeto** en la lista desplegable que aparece para asignar el tipo **ActivityAction\<objeto >** al argumento.  
  
10. Arrastre un <xref:System.Activities.Statements.While> actividad desde la **flujo de Control** sección del cuadro de herramientas a la superficie del diseñador.  
  
11. Seleccione el <xref:System.Activities.Statements.While> actividad y seleccione el **Variables** ficha.  
  
12. Seleccione **crear Variable**. Nombre de la nueva variable **índice**.  
  
13. En el **tipo de Variable** columna, seleccione **Int32**. Deje el **ámbito** como **mientras**y el **predeterminado** columna en blanco.  
  
14. Establecer el **condición** propiedad de la <xref:System.Activities.Statements.While> actividad **índice < Items.Length;**.  
  
15. Arrastre un <xref:System.Activities.Statements.InvokeDelegate> actividad desde el **primitivas** sección del cuadro de herramientas para el **cuerpo** de la <xref:System.Activities.Statements.While> actividad.  
  
16. Seleccione **cuerpo** en la lista desplegable de delegado.  
  
17. En el **propiedades** cuadrícula para el <xref:System.Activities.Statements.InvokeDelegate> actividad, haga clic en el **...** botón en el **argumentos de delegado** propiedad.  
  
18. En el **valor** columna del argumento denominado **argumento**, escriba **elementos [índice]**. Haga clic en **Aceptar** para cerrar el **DelegateArguments** cuadro de diálogo.  
  
19. Arrastre una actividad <xref:System.Activities.Statements.Assign> sobre la línea horizontal bajo la actividad <xref:System.Activities.Statements.InvokeDelegate>. El <xref:System.Activities.Statements.Assign> se creará la actividad y un <xref:System.Activities.Statements.Sequence> actividad se crearán automáticamente para que contenga las dos actividades en el **cuerpo** sección de la **MyForEach** actividad. La secuencia es necesaria porque el **cuerpo** sección solo puede contener una sola actividad. La creación automática de una nueva actividad <xref:System.Activities.Statements.Sequence> es una nueva característica de [!INCLUDE[net_v45](../includes/net-v45-md.md)].  
  
20. Establecer el **a** propiedad de la <xref:System.Activities.Statements.Assign> actividad **índice**. Establecer el **valor** propiedad de la **asignar** actividad **index+1**.  
  
 Personalizado **MyForEach** actividad ahora invocará una actividad arbitraria una vez para cada valor pasado en ella mediante la **elementos** colección, con los valores de la colección como entradas para la actividad.  
  
### <a name="use-the-custom-activity-in-a-workflow"></a>Usar la actividad personalizada en un flujo de trabajo  
  
1.  Compile el proyecto presionando **Ctrl + Mayús + B**.  
  
2.  En **el Explorador de soluciones**, abra **Workflow1.xaml** en el diseñador.  
  
3.  Arrastre un **MyForEach** actividad desde el cuadro de herramientas a la superficie del diseñador. La actividad estará en una sección del cuadro de herramientas con el mismo nombre que el proyecto.  
  
4.  Establecer el **elementos** propiedad de la **MyForEach** actividad **new Object [] {1, "abc"}**.  
  
5.  Arrastre un <xref:System.Activities.Statements.WriteLine> actividad desde la **primitivas** sección del cuadro de herramientas para el **Delegate: cuerpo** sección de la **MyForEach** actividad.  
  
6.  Establecer el **texto** propiedad de la <xref:System.Activities.Statements.WriteLine> actividad **Argument.ToString ()**.  
  
 Cuando se ejecuta el flujo de trabajo, la consola mostrará lo siguiente:  
  
 **1**   
**ABC**