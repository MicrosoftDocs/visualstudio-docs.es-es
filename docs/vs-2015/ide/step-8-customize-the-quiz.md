---
title: 'Paso 8: Personalizar la prueba | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ded65e85a2ae11e96c21fdd852ea12daa4bbcdf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299987"
---
# <a name="step-8-customize-the-quiz"></a>Paso 8: Personalizar la prueba
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En la última parte del tutorial, explorará algunas maneras de personalizar la prueba y ampliar sus conocimientos. Por ejemplo, piense en cómo el programa crea problemas de división aleatorios para los que la respuesta nunca es una fracción. Para obtener más información, cambie el color del control `timeLabel` y proporcione al usuario alguna sugerencia.

### <a name="to-customize-the-quiz"></a>Para personalizar la prueba

- Cuando solo queden cinco segundos en una prueba, cambie el color del control **timeLabel** a rojo estableciendo su propiedad **BackColor** (`timeLabel.BackColor = Color.Red;`). Restablezca el color cuando la prueba haya terminado.

- Proporcione una sugerencia al jugador reproduciendo un sonido cuando especifique una respuesta correcta en un control NumericUpDown. (Tendrá que escribir un controlador de eventos para el evento `ValueChanged()` de cada control, que se desencadena cada vez que el jugador cambia el valor del control.)

### <a name="to-continue-or-review"></a>Para continuar o revisar

- Para ir al siguiente tutorial, vea [Tutorial 3: Crear un juego de formar parejas](../ide/tutorial-3-create-a-matching-game.md).

- Para volver al paso anterior del tutorial, vea [Paso 7: Agregar problemas de multiplicación y división](../ide/step-7-add-multiplication-and-division-problems.md).
