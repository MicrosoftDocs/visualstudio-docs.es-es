---
title: 'Paso 8: Personalizar la prueba | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-acquisition
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 876a09ddd4c54c1b4e22886110ca9a8ac76c65f4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="step-8-customize-the-quiz"></a>Paso 8: Personalizar la prueba
En la última parte del tutorial, explorará algunas maneras de personalizar la prueba y ampliar sus conocimientos. Por ejemplo, piense en cómo el programa crea problemas de división aleatorios para los que la respuesta nunca es una fracción. Para obtener más información, cambie el color del control `timeLabel` y proporcione al usuario alguna sugerencia.  
  
### <a name="to-customize-the-quiz"></a>Para personalizar la prueba  
  
-   Cuando solo queden cinco segundos en una prueba, cambie el color del control **timeLabel** a rojo estableciendo su propiedad **BackColor** (`timeLabel.BackColor = Color.Red;`). Restablezca el color cuando la prueba haya terminado.  
  
-   Proporcione una sugerencia al jugador reproduciendo un sonido cuando especifique una respuesta correcta en un control NumericUpDown. (Tendrá que escribir un controlador de eventos para el evento `ValueChanged()` de cada control, que se desencadena cada vez que el jugador cambia el valor del control.)  
  
### <a name="to-continue-or-review"></a>Para continuar o revisar  
  
-   Para descargar una versión completa de la prueba, vea [Ejemplo completo del tutorial de prueba matemática](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
-   Para ir al siguiente tutorial, vea [Tutorial 3: Crear un juego de formar parejas](../ide/tutorial-3-create-a-matching-game.md).  
  
-   Para volver al paso anterior del tutorial, vea [Paso 7: Agregar problemas de multiplicación y división](../ide/step-7-add-multiplication-and-division-problems.md).