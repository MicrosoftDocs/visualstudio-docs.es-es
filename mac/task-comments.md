---
title: Comentarios de tareas
description: Agregar comentarios de tarea en el código
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 44d82becfbf3a16ccd2158ac05e171e8530cd721
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224229"
---
# <a name="task-comments"></a>Comentarios de tareas

Al escribir código, es una práctica estándar comentar de forma explícita el código sin terminar o cuestionable o las soluciones rápidas con advertencias. Los tokens de señal predeterminados que proporciona Visual Studio para Mac son TODO, HACK, FIXME y UNDONE. Se pueden definir tokens personalizados en **Visual Studio > Preferencias... > Entorno > Tareas**, como se muestra en la siguiente imagen:

 ![Preferencias de la lista de tareas](media/source-editor-image10.png)

Para agregar un nuevo comentario de tarea, agregue un comentario que incluya la palabra clave tarea. Por ejemplo:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio para Mac dirige la atención a estos marcadores al resaltarlos en el panel Lista de tareas, que se muestra al ir a **Vista > Paneles > Tarea**:

![Panel Lista de tareas](media/source-editor-image11.png)