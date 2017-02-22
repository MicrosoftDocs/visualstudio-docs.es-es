---
title: "Definir y consumir delegados de actividad en el Dise&#241;ador de flujo de trabajo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "sdanie"
manager: "erikre"
---
# Definir y consumir delegados de actividad en el Dise&#241;ador de flujo de trabajo
[!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] incluye un nuevo diseñador estándar para la actividad <xref:System.Activities.Statements.InvokeDelegate>.Este diseñador se puede usar para asignar delegados a la actividad que se derivan de <xref:System.Activities.ActivityDelegate>, como <xref:System.Activities.ActivityAction> o <xref:System.Activities.ActivityFunc%601>.  
  
### Definir un delegado de actividad  
  
1.  En [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], seleccione **Archivo**, **NuevoProyecto**.Seleccione el nodo **Flujo de trabajo** a la izquierda y la plantilla de **Aplicación de consola de flujo de trabajo** a la derecha.Asigne nombre al proyecto \(si lo desea\) y haga clic en **Aceptar**.  
  
2.  Haga clic con el botón secundario en el proyecto en el **Explorador de soluciones** y, a continuación, seleccione**Agregar**, **Nuevo elemento...**.Seleccione el nodo **Flujo de trabajo** de la izquierda y la plantilla **Actividad** de la derecha.Asigne a la nueva actividad el nombre **MyForEach.xaml** y haga clic en **Aceptar**.La actividad se abrirá en el diseñador de flujo de trabajo.  
  
3.  En el diseñador de flujo de trabajo, haga clic en la pestaña **Argumentos**.  
  
4.  Haga clic en **Crear argumento**.Asigne al nuevo argumento el nombre **Elementos**.  
  
5.  En la columna **Tipo de argumento**, seleccione **Matriz de \[T\]**.  
  
6.  En el explorador de tipo, seleccione **Objeto**.Haga clic en **Aceptar**.  
  
7.  Haga clic de nuevo en **Crear argumento**.Asigne al nuevo argumento el nombre **Cuerpo**.En la columna **Dirección** para el nuevo argumento, seleccione **Propiedad**.  
  
8.  En la columna Tipo de argumento, seleccione **Buscar tipos…**.  
  
9. En el explorador de tipo, escriba **ActivityAction** en el campo **Nombre de tipo**.Seleccione **ActivityAction\<T\>** en la vista de árbol.Seleccione **Objeto** en el desplegable que aparece para asignar el tipo **ActivityAction\<Object\>** al argumento.  
  
10. Arrastre una actividad <xref:System.Activities.Statements.While> de la sección **Flujo de control** del cuadro de herramientas a la superficie del diseñador.  
  
11. Seleccione la actividad <xref:System.Activities.Statements.While> y seleccione la pestaña **Variables**.  
  
12. Seleccione **Crear variable**.Asigne a la nueva variable el nombre **Índice**.  
  
13. En la columna **Tipo de variable**, seleccione **Int32**.Deje **Ámbito** como **While** y la columna **Valor predeterminado** en blanco.  
  
14. Establezca la propiedad **Condición** de la actividad <xref:System.Activities.Statements.While> en **index \< Items.Length;** .  
  
15. Arrastre una actividad <xref:System.Activities.Statements.InvokeDelegate> de la sección **Primitivas** del cuadro de herramientas al **Cuerpo** de la actividad <xref:System.Activities.Statements.While>.  
  
16. Seleccione **Cuerpo** en el desplegable de delegado.  
  
17. En la cuadrícula de **Propiedades** para la actividad <xref:System.Activities.Statements.InvokeDelegate>, haga clic en el botón **…** en la propiedad **Argumentos de delegado**.  
  
18. En la columna **Valor** del argumento denominado **Argumento**, escriba en **Elementos\[Índice\]**.Haga clic en **Aceptar** para cerrar el cuadro de diálogo **DelegateArguments**.  
  
19. Arrastre una actividad <xref:System.Activities.Statements.Assign> sobre la línea horizontal bajo la actividad <xref:System.Activities.Statements.InvokeDelegate>.La actividad <xref:System.Activities.Statements.Assign> se creará y se creará automáticamente una actividad <xref:System.Activities.Statements.Sequence> para contener las dos actividades en la sección **Cuerpo** de la actividad **MyForEach**.La secuencia es necesaria porque la sección **Cuerpo** puede contener una sola actividad.La creación automática de una nueva actividad <xref:System.Activities.Statements.Sequence> es una nueva característica de [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].  
  
20. Establezca la propiedad **To** de la actividad <xref:System.Activities.Statements.Assign> en **index**.Establezca la propiedad **Value** de la actividad **Assign** en **index\+1**.  
  
 La actividad personalizada **MyForEach** ahora invocará una actividad arbitraria una vez por cada valor pasado en ella mediante la colección **Items**, con los valores de la colección como entradas para la actividad.  
  
### Usar la actividad personalizada en un flujo de trabajo  
  
1.  Compile el proyecto presionando **CTRL\+MAYÚS\+B**.  
  
2.  En el **Explorador de soluciones**, abra **Workflow1.xaml** en el diseñador.  
  
3.  Arrastre una actividad **MyForEach** desde el cuadro de herramientas a la superficie del diseñador.La actividad estará en una sección del cuadro de herramientas con el mismo nombre que el proyecto.  
  
4.  Establezca la propiedad **Items** de la actividad **MyForEach** en **new Object\[\] {1, "abc"}**.  
  
5.  Arrastre una actividad <xref:System.Activities.Statements.WriteLine> desde la sección **Primitivas** del cuadro de herramientas a la sección **Delegate:Cuerpo** de la actividad **MyForEach**.  
  
6.  Establezca la propiedad **Text** de la actividad <xref:System.Activities.Statements.WriteLine> en **Argument.ToString\(\)**.  
  
 Cuando se ejecuta el flujo de trabajo, la consola mostrará lo siguiente:  
  
 **1**   
**abc**