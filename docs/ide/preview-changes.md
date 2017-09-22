---
title: Vista previa de cambios | Microsoft Docs
ms.custom: 
ms.date: 12/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e15c00f6-3e22-49b8-8269-69e4c8be8040
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.codefix.previewchanges
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 14e6961d6db557e77687eef17aae9b16f5a4d706
ms.openlocfilehash: eb49815ed120ee4ff65dfc04764282f1ac6d1ff8
ms.contentlocale: es-es
ms.lasthandoff: 02/22/2017

---

# <a name="preview-changes"></a>Vista previa de cambios

Visual Studio incluye varias herramientas de *Acciones rápidas* o *Refactorización* que permiten obtener una vista previa de los cambios que se van a realizar en el proyecto antes de aceptarlos.  Esto tiene lugar en la ventana **Vista previa de los cambios**.  Por ejemplo, aquí en la ventana **Vista previa de los cambios** se muestra qué se cambiará durante una refactorización de cambio de nombre en un proyecto de C#:

![Vista previa de cambios](media/previewchanges.png)

En la mitad superior de la ventana se muestran las líneas específicas que se cambiarán, cada una con una casilla.  Puede activar o desactivar cada casilla si quiere aplicar de manera selectiva la refactorización solo en líneas específicas.

En la mitad inferior de la ventana se muestra el código con formato del proyecto que se cambiará, con las áreas afectadas resaltadas.  Al seleccionar la línea específica en la mitad superior de la ventana, se resaltará la línea correspondiente en la mitad inferior.  Esto le permite ir rápidamente a la línea apropiada y ver el código circundante.

Después de revisar los cambios, haga clic en el botón **Aplicar** para aceptar esos cambios o haga clic en el botón **Cancelar** para dejar las cosas tal y como estaban.

## <a name="see-also"></a>Vea también  
[Refactorización en Visual Studio](../ide/refactoring-in-visual-studio.md)

