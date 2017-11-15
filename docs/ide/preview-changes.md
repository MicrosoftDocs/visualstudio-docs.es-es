---
title: Vista previa de cambios | Microsoft Docs
ms.custom: 
ms.date: 12/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e15c00f6-3e22-49b8-8269-69e4c8be8040
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.codefix.previewchanges
ms.openlocfilehash: 52555d0bc112dae41f189fd9f29711da365fd59c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="preview-changes"></a>Vista previa de cambios

Visual Studio incluye varias herramientas de *Acciones rápidas* o *Refactorización* que permiten obtener una vista previa de los cambios que se van a realizar en el proyecto antes de aceptarlos.  Esto tiene lugar en la ventana **Vista previa de los cambios**.  Por ejemplo, aquí en la ventana **Vista previa de los cambios** se muestra qué se cambiará durante una refactorización de cambio de nombre en un proyecto de C#:

![Vista previa de cambios](media/previewchanges.png)

En la mitad superior de la ventana se muestran las líneas específicas que se cambiarán, cada una con una casilla.  Puede activar o desactivar cada casilla si quiere aplicar de manera selectiva la refactorización solo en líneas específicas.

En la mitad inferior de la ventana se muestra el código con formato del proyecto que se cambiará, con las áreas afectadas resaltadas.  Al seleccionar la línea específica en la mitad superior de la ventana, se resaltará la línea correspondiente en la mitad inferior.  Esto le permite ir rápidamente a la línea apropiada y ver el código circundante.

Después de revisar los cambios, haga clic en el botón **Aplicar** para aceptar esos cambios o haga clic en el botón **Cancelar** para dejar las cosas tal y como estaban.

## <a name="see-also"></a>Vea también  
[Refactorización en Visual Studio](../ide/refactoring-in-visual-studio.md)
