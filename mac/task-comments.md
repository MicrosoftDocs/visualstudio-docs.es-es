---
title: Comentarios de tareas
description: ''
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: c119af47cc3b592033a68b0ec543afa86140c77a
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="task-comments"></a>Comentarios de tareas

Al escribir código, es una práctica estándar comentar de forma explícita el código sin terminar o cuestionable o las soluciones rápidas con advertencias. Los tokens de señal predeterminados que proporciona Visual Studio para Mac son TODO, HACK, FIXME y UNDONE. Se pueden definir tokens personalizados en **Visual Studio > Preferencias... > Entorno > Tareas**, como se muestra en la siguiente imagen:

 ![Preferencias de la lista de tareas](media/source-editor-image10.png)

Para agregar un nuevo comentario de tarea, agregue un comentario que incluya la palabra clave tarea. Por ejemplo:

```
//TODO: Finish this for all properties.
```

Visual Studio para Mac dirige la atención a estos marcadores al resaltarlos en el panel Lista de tareas, que se muestra al ir a **Vista > Paneles > Tarea**:

![Panel Lista de tareas](media/source-editor-image11.png)