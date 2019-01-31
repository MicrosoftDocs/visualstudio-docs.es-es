---
title: Cuadro de diálogo Lista de tareas, Entorno, Opciones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
- VS.ToolsOptionsPag.Environment.Task_List
- VS.ToolsOptionsPages.Environment.TaskList
- VS.Environment.Task List
helpviewer_keywords:
- Token List
- tokens
- icons, in Task List
- Task List, customizing environment
- Options dialog box, Task List environment
- exclamation points
- comments, comment tasks in Task List
- tokens, and the Task List
- Task List, comment tasks
ms.assetid: 88327e04-fa3e-48db-995b-ad89e0dc4ed2
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94f0fc19c84a5e86dbfff27a88b179f6a9bfb566
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795489"
---
# <a name="task-list-environment-options-dialog-box"></a>Lista de tareas, Entorno, Opciones (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Esta página Opciones permite agregar, eliminar y cambiar los tokens de comentarios que generan los avisos de **Lista de tareas**. Para mostrar estas opciones, seleccione **Opciones** en el menú **Herramientas**, expanda la carpeta **Entorno** y elija **Lista de tareas**.  
  
## <a name="task-list-options"></a>Opciones de lista de tareas  
 Confirmar eliminación de tareas  
 Cuando se selecciona, se muestra un cuadro de mensaje cada vez que se elimina una tarea de usuario de la **Lista de tareas**, lo que le permite confirmar la eliminación. Esta opción está seleccionada de forma predeterminada.  
  
> [!NOTE]
>  Para eliminar un comentario de tarea, utilice el vínculo para buscar el comentario y, a continuación, elimínelo del código.  
  
 Mostrar solo nombres de archivo  
 Cuando se selecciona, la columna **Archivo** de la **Lista de tareas** muestra solo los nombres de archivos que se van a editar, no sus rutas de acceso completas.  
  
## <a name="tokens"></a>tokens  
 Al insertar un comentario en el código cuyo texto comienza con un token de la **Lista de tokens**, la **Lista de tareas** mostrará el comentario como nueva entrada cada vez que se abra el archivo para su edición. Haga clic en la entrada **Lista de tareas** para saltar directamente a la línea de comentario del código. Para obtener más información, consulte [Usar la Lista de tareas](../../ide/using-the-task-list.md).  
  
 Lista de tokens  
 Muestra una lista de tokens y permite agregar o quitar tokens personalizados. Los tokens de comentarios distinguen entre mayúsculas y minúsculas en Visual C# y Visual C++, pero no en Visual Basic.  
  
> [!NOTE]
>  Si no escribe el token deseado exactamente como aparece en la **Lista de tokens**, no se mostrará una tarea de comentario en la **Lista de tareas**.  
  
 Prioridad  
 Establece la prioridad de las tareas que utilizan el token seleccionado. A los comentarios sobre tareas que comienzan con este token se les asigna automáticamente la prioridad designada en la **Lista de tareas**.  
  
 nombre  
 Escriba la cadena de token. Esto habilita el botón **Agregar**. En **Agregar**, esta cadena está incluida en la **Lista de tokens** y los comentarios que comienzan por este nombre se mostrarán en la **Lista de tareas**.  
  
 Add  
 Se habilita al escribir un nuevo **Nombre**. Haga clic para agregar una nueva cadena de tokens utilizando los valores especificados en los campos **Nombre** y **Prioridad**.  
  
 Eliminar  
 Haga clic en esta opción para eliminar el token seleccionado en la **Lista de tokens**. No puede eliminar los tokens de comentario predeterminados.  
  
 Cambio  
 Haga clic aquí para modificar un token existente utilizando los valores especificados en los campos **Nombre** y **Prioridad**.  
  
> [!NOTE]
>  No puede eliminar el token de comentario predeterminado ni cambiar su nombre, pero puede cambiar su nivel de prioridad.  
  
## <a name="see-also"></a>Vea también  
 [Usar la Lista de tareas](../../ide/using-the-task-list.md)   
 [Establecer marcadores en el código](../../ide/setting-bookmarks-in-code.md)   
 [Opciones de entorno (Cuadro de diálogo)](../../ide/reference/environment-options-dialog-box.md)
