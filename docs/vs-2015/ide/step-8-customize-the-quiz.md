---
title: 'Paso 8: Personalizar la prueba | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 72e630a3d065e196d33919045316fad27c912750
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581652"
---
# <a name="step-8-customize-the-quiz"></a>Paso 8: Personalizar la prueba
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [paso 8: personalizar la prueba](https://docs.microsoft.com/visualstudio/ide/step-8-customize-the-quiz).  
  
En la última parte del tutorial, explorará algunas maneras de personalizar la prueba y ampliar sus conocimientos. Por ejemplo, piense en cómo el programa crea problemas de división aleatorios para los que la respuesta nunca es una fracción. Para obtener más información, cambie el color del control `timeLabel` y proporcione al usuario alguna sugerencia.  
  
### <a name="to-customize-the-quiz"></a>Para personalizar la prueba  
  
-   Cuando solo queden cinco segundos en una prueba, cambie el color del control **timeLabel** a rojo estableciendo su propiedad **BackColor** (`timeLabel.BackColor = Color.Red;`). Restablezca el color cuando la prueba haya terminado.  
  
-   Proporcione una sugerencia al jugador reproduciendo un sonido cuando especifique una respuesta correcta en un control NumericUpDown. (Tendrá que escribir un controlador de eventos para el evento `ValueChanged()` de cada control, que se desencadena cada vez que el jugador cambia el valor del control.)  
  
### <a name="to-continue-or-review"></a>Para continuar o revisar  
  
-   Para descargar una versión completa de la prueba, vea [Ejemplo completo del tutorial de prueba matemática](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
-   Para ir al siguiente tutorial, vea [Tutorial 3: Crear un juego de formar parejas](../ide/tutorial-3-create-a-matching-game.md).  
  
-   Para volver al paso anterior del tutorial, vea [Paso 7: Agregar problemas de multiplicación y división](../ide/step-7-add-multiplication-and-division-problems.md).



