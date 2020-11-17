---
title: Comentarios de tareas
description: Agregar comentarios de tarea en el código
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 02eacb312931d941b716ee65f91cd478eac8bb8a
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493535"
---
# <a name="task-comments"></a>Comentarios de tareas

Al escribir código, un procedimiento habitual es comentar de forma explícita el código sin terminar o cuestionable o las soluciones rápidas con advertencias. Los tokens de señal predeterminados que proporciona Visual Studio para Mac son TODO, HACK, FIXME y UNDONE. Se pueden definir tokens personalizados en **Visual Studio > Preferencias > Entorno > Tareas**, como se muestra en la siguiente imagen:

![Preferencias de la lista de tareas](media/source-editor-image10.png)

Para agregar un nuevo comentario de tarea, agregue un comentario que incluya la palabra clave tarea. Por ejemplo:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio para Mac dirige la atención a estos marcadores al resaltarlos en la ventana **Lista de tareas**, que se puede mostrar mediante el menú **Vista > Tareas**:

![Ventana Lista de tareas, que muestra un solo elemento TODO](media/source-editor-image11.png)

## <a name="see-also"></a>Consulte también

- [Uso de la lista de tareas (Visual Studio en Windows)](/visualstudio/ide/using-the-task-list)