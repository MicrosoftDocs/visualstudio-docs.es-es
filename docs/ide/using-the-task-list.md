---
title: "Usar la Lista de tareas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TaskListWindow"
  - "VS.TaskList"
  - "tasklist"
helpviewer_keywords: 
  - "lista de tareas"
  - "Visual Studio, lista de tareas"
ms.assetid: f46a75a8-47b3-4cb6-bb59-b72e3356a664
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Usar la Lista de tareas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use la **Lista de tareas** para hacer un seguimiento de los comentarios de código que usan tokens como `TODO` y `HACK` \(o tokens personalizados\) y administrar los accesos directos que le llevarán directamente a una ubicación predefinida del código. Haga clic en el elemento de la lista para ir a su ubicación en el código fuente.  
  
 En este tema:  
  
-   [La ventana Lista de tareas](../ide/using-the-task-list.md#taskListWindow)  
  
-   [Tareas de usuario](../ide/using-the-task-list.md#userTasks)  
  
-   [Tokens y comentarios](../ide/using-the-task-list.md#tokensComments)  
  
-   [Tokens personalizados](../ide/using-the-task-list.md#customTokens)  
  
-   [Comentarios TODO en C++](../ide/using-the-task-list.md#cppComments)  
  
-   [Accesos directos](../ide/using-the-task-list.md#shortcuts)  
  
##  <a name="taskListWindow"></a> La ventana Lista de tareas  
 Cuando la ventana **Lista de tareas** está abierta, aparece en la parte inferior de la ventana de la aplicación.  
  
#### Para abrir la Lista de tareas  
  
-   En el menú **Ver**, elija **Lista de tareas** \(teclado: Ctrl\+\\, T\).  
  
     ![Ventana Lista de tareas](../ide/media/vs2015_task_list.png "vs2015\_task\_list")  
  
#### Para cambiar el criterio de ordenación de la lista  
  
-   Haga clic en el encabezado de cualquier columna. Para refinar los resultados de la búsqueda, presione la tecla Mayúsculas y haga clic en otro encabezado de columna.  
  
     Como alternativa, en el menú contextual, elija **Ordenar por** y elija un encabezado. Para refinar los resultados de la búsqueda, presione la tecla Mayúsculas y elija un segundo encabezado de columna.  
  
#### Para mostrar u ocultar columnas  
  
-   En el menú contextual, elija **Mostrar columnas**. Elija las columnas que desee mostrar u ocultar.  
  
#### Para cambiar el orden de las columnas  
  
-   Arrastre cualquier encabezado de columna hasta la ubicación que desee.  
  
##  <a name="userTasks"></a> Tareas de usuario  
 Se ha quitado la característica de tareas de usuario en Visual Studio 2015. Cuando se abre una solución que tiene datos de tareas de usuario de Visual Studio 2013 y versiones anteriores en Visual Studio 2015, dichos datos no se verán afectados en el archivo .suo, pero las tareas de usuario no se mostrarán en la lista de tareas.  
  
 Si desea seguir teniendo acceso y actualizar los datos de tareas de usuario, debe abrir el proyecto en Visual Studio 2013 y copiar el contenido de las tareas de usuario en la herramienta de administración de proyecto preferido \(por ejemplo, Team Foundation Server\).  
  
##  <a name="tokensComments"></a> Tokens y comentarios  
 Un comentario en el código precedido de un marcador de comentario y un token predefinido aparecerán en la ventana **Lista de tareas**. Por ejemplo, el siguiente comentario de C\# tiene tres partes distintas:  
  
-   El marcador de comentario \(`//`\)  
  
-   El token, por ejemplo \(`TODO`\)  
  
-   El comentario \(el resto del texto\)  
  
```  
// TODO: Load state from previously suspended application  
```  
  
 Dado que `TODO` es un token predefinido, este comentario aparece como una tarea `TODO` en la lista.  
  
###  <a name="customTokens"></a> Tokens personalizados  
 De forma predeterminada, Visual Studio incluye los tokens siguientes: HACK, TODO, UNDONE, NOTE. Estos no distinguen mayúsculas de minúsculas.  
  
 También puede crear tokens propios personalizados.  
  
##### Para crear un token personalizado  
  
1.  En el menú **Herramientas**, elija **Opciones**.  
  
2.  Abra la carpeta **Entorno** y, a continuación, elija **Lista de tareas**.  
  
     Se muestra [Lista de tareas, Entorno, Opciones \(Cuadro de diálogo\)](../ide/reference/task-list-environment-options-dialog-box.md).  
  
     ![Lista de tareas de Visual Studio](~/docs/ide/media/vs2015_task_list_options.png "vs2015\_task\_list\_options")  
  
3.  En la categoría **Tokens**, en el cuadro de texto **Nombre**, escriba el nombre del token; por ejemplo, "BUG".  
  
4.  En la lista desplegable **Prioridad**, elija una prioridad predeterminada para el nuevo token. Elija el botón de **Agregar**.  
  
###  <a name="cppComments"></a> Comentarios TODO en C\+\+  
 De forma predeterminada, los comentarios TODO en C\+\+ no se muestran en la ventana **Lista de tareas**. Esto se puede cambiar:  
  
##### Para desactivar los comentarios TODO en C\+\+  
  
1.  En el menú **Herramientas**, vaya a **Opciones &#124; Editor de texto &#124; C\/C\+\+ &#124; Vista &#124; Enumerar tareas de comentario** y establezca el valor como falso.  
  
2.  En el cuadro de diálogo **Opciones** abra el **Editor de texto**.  
  
3.  En **C\/C\+\+**, elija **Ver** y establezca **Enumerar tareas de comentario** como **Falso**.  
  
##  <a name="shortcuts"></a> Accesos directos  
 Un *acceso directo* es un marcador en el código al que se le realiza el seguimiento en la **Lista de tareas**; su icono es diferente al de los marcadores normales. Haga doble clic en el acceso directo en la **Lista de tareas** para ir a la ubicación correspondiente en el código.  
  
 ![Icono de acceso directo de Visual Studio](../ide/media/vs2015_task_list_bookmark.png "vs2015\_task\_list\_bookmark")  
  
#### Para crear un acceso directo  
  
-   Inserte el puntero donde desee colocar un acceso directo en el código. Elija **Editar &#124; Marcadores &#124; Agregar acceso directo a lista de tareas** o presione \(teclado: CTRL \+ K, CTRL \+ H\).  
  
     Para navegar por los accesos directos en el código, elija un acceso directo de la lista y, después, elija **Tarea siguiente** o **Tarea anterior** en el menú contextual.  
  
## Vea también  
 [Lista de tareas, Entorno, Opciones \(Cuadro de diálogo\)](../ide/reference/task-list-environment-options-dialog-box.md)