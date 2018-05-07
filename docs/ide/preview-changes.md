---
title: Vista previa de cambios de código en Visual Studio
ms.date: 12/16/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.codefix.previewchanges
ms.workload:
- multiple
ms.openlocfilehash: dfb9ff26ca20060a8df9a0b3a81783b60e0b46f3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="preview-changes-window"></a>Ventana para obtener vista previa de cambios

Visual Studio incluye varias herramientas de *Acciones rápidas* o *Refactorización* que permiten obtener una vista previa de los cambios que se van a realizar en el proyecto antes de aceptarlos. Esto tiene lugar en la ventana **Vista previa de los cambios**.  Por ejemplo, aquí en la ventana **Vista previa de los cambios** se muestra qué se cambiará durante una refactorización de cambio de nombre en un proyecto de C#:

![Vista previa de cambios](media/previewchanges.png)

En la mitad superior de la ventana se muestran las líneas específicas que se cambiarán, cada una con una casilla. Puede activar o desactivar cada casilla si quiere aplicar de manera selectiva la refactorización solo en líneas específicas.

En la mitad inferior de la ventana se muestra el código con formato del proyecto que se cambiará, con las áreas afectadas resaltadas. Al seleccionar la línea específica en la mitad superior de la ventana, se resaltará la línea correspondiente en la mitad inferior. Esto le permite ir rápidamente a la línea apropiada y ver el código circundante.

Después de revisar los cambios, haga clic en el botón **Aplicar** para aceptar esos cambios o haga clic en el botón **Cancelar** para dejar las cosas tal y como estaban.

## <a name="see-also"></a>Vea también

- [Refactorización en Visual Studio](../ide/refactoring-in-visual-studio.md)
- [Acciones rápidas](../ide/quick-actions.md)
