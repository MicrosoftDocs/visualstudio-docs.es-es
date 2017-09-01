---
title: Comentarios de tareas
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 973e7b627a7b5c121ff388874577fe59c45529d7
ms.contentlocale: es-es
ms.lasthandoff: 08/11/2017

---

# <a name="task-comments"></a>Comentarios de tareas

Al escribir código, es una práctica estándar comentar de forma explícita el código sin terminar o cuestionable o las soluciones rápidas con advertencias. Los tokens de señal predeterminados proporcionados por Visual Studio para Mac son TODO, HACK, FIXME y UNDONE, aunque se pueden definir tokens personalizados en **Visual Studio > Preferencias... > Entorno > Tareas**, como se muestra a continuación:

 ![Preferencias de la lista de tareas](media/source-editor-image10.png)

Para agregar un nuevo comentario de tarea, agregue un comentario que incluya la palabra clave tarea. Por ejemplo:

```
//TODO: Finish this for all properties.
```

Visual Studio para Mac dirige la atención a estos marcadores al resaltarlos en el panel Lista de tareas, que se muestra al ir a **Vista > Paneles > Tarea**:

![Panel Lista de tareas](media/source-editor-image11.png)
