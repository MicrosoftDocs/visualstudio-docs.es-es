---
title: Lista de tareas, Entorno, Opciones (Cuadro de diálogo)
description: Obtenga información sobre cómo usar la página de Lista de tareas de la sección Entorno para agregar, eliminar y cambiar los tokens de comentarios que generan recordatorios de Lista de tareas.
ms.custom: SEO-VS-2020
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59eba4addc21c47db19de212c527e744428973f4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838371"
---
# <a name="options-dialog-box-environment--task-list"></a>Cuadro de diálogo Opciones: Entorno \> Lista de tareas

Esta página Opciones permite agregar, eliminar y cambiar los tokens de comentarios que generan los avisos de **Lista de tareas**. Para mostrar estas opciones, seleccione **Opciones** en el menú **Herramientas**, expanda la carpeta **Entorno** y elija **Lista de tareas**.

## <a name="task-list-tokens"></a>Tokens de la Lista de tareas

Al insertar un comentario en el código cuyo texto comienza con un token de la **Lista de tokens**, la **Lista de tareas** mostrará el comentario como nueva entrada cada vez que se abra el archivo para su edición. Haga clic en una entrada de la **Lista de tareas** para saltar directamente a la línea de comentario del código. Para obtener más información, consulte [Usar la Lista de tareas](../../ide/using-the-task-list.md).

Token List\
Muestra una lista de tokens y permite agregar o quitar tokens personalizados. Los tokens de comentarios distinguen entre mayúsculas y minúsculas en C# y C++, pero no en Visual Basic.

> [!NOTE]
> Si no escribe el token deseado exactamente como aparece en la lista de tokens, no se mostrará una tarea de comentario en la **Lista de tareas**.

Priority\
Establece la prioridad de las tareas que utilizan el token seleccionado (baja, normal o alta). A los comentarios sobre tareas que comienzan con este token se les asigna automáticamente la prioridad designada en la **Lista de tareas**.

Name\
Escriba aquí la cadena de token y haga clic en **Agregar** para agregar la cadena a la lista de tokens.

Add\
Se habilita al escribir un nuevo **Nombre**. Haga clic para agregar una nueva cadena de tokens utilizando los valores especificados en los campos **Nombre** y **Prioridad**.

Delete\
Haga clic en esta opción para eliminar el token seleccionado en la lista de tokens. No puede eliminar los tokens de comentario predeterminados.

Change\
Haga clic aquí para modificar un token existente utilizando los valores especificados en los campos **Nombre** y **Prioridad**.

> [!NOTE]
> No puede eliminar el token de comentario predeterminado ni cambiar su nombre, pero puede cambiar su nivel de prioridad.

## <a name="see-also"></a>Vea también

- [Uso de la lista de tareas](../../ide/using-the-task-list.md)
- [Establecer marcadores en el código](../../ide/setting-bookmarks-in-code.md)
