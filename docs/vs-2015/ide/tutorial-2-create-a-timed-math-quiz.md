---
title: 'Tutorial 2: Crear una prueba matemática cronometrada | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8b0b7a5949ab8fe624a087a1e024367f896ddb99
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884893"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Tutorial 2: Crear una prueba matemática cronometrada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial, se compila un juego de prueba matemática en el que el jugador debe responder a cuatro problemas aritméticos aleatorios en un tiempo especificado. Aprenderá a:  
  
- Generar números aleatorios mediante la clase `Random`.  
  
- Generar eventos que se producirán en un momento concreto con un control **Timer**.  
  
- Controlar el flujo del programa con instrucciones `if else`.  
  
- Realizar operaciones aritméticas básicas en el código.  
  
  Cuando termine, la prueba matemática se parecerá a la siguiente imagen, pero tendrá otros números.  
  
  ![Prueba matemática con cuatro problemas](../ide/media/express-finishedquiz.png "Express_FinishedQuiz")  
  Juego de prueba matemática que creará en este tutorial  
  
  Para descargar una versión completa de la prueba, vea [Ejemplo completo del tutorial de prueba matemática](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
> [!NOTE]
>  En este tutorial, se trata tanto Visual C# como Visual Basic, por lo que deberá centrarse en la información específica del lenguaje de programación que use.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Paso 1: Crear un proyecto y agregar etiquetas al formulario](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Comience creando el proyecto, cambiando las propiedades y agregando controles `Label`.|  
|[Paso 2: Crear un problema de suma aleatoria](../ide/step-2-create-a-random-addition-problem.md)|Cree un problema de suma y use la clase `Random` para generar números aleatorios.|  
|[Paso 3: Agregar un temporizador de cuenta atrás](../ide/step-3-add-a-countdown-timer.md)|Agregue un temporizador de cuenta atrás para poder limitar el tiempo de la prueba.|  
|[Paso 4: Agregar el método CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Agregue un método para comprobar si el jugador ha escrito una respuesta correcta para el problema.|  
|[Paso 5: Agregar controladores de eventos Enter para los controles NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Agregue controladores de eventos para que sea más fácil jugar.|  
|[Paso 6: Agregar un problema de resta](../ide/step-6-add-a-subtraction-problem.md)|Agregue un problema de resta que genere números aleatorios, utilice el temporizador y compruebe si las respuestas son correctas.|  
|[Paso 7: Agregar problemas de multiplicación y división](../ide/step-7-add-multiplication-and-division-problems.md)|Agregue problemas de multiplicación y división que generen números aleatorios, utilicen el temporizador y se comprueban para ver si las respuestas son correctas.|  
|[Paso 8: Personalizar la prueba](../ide/step-8-customize-the-quiz.md)|Pruebe con otras características, como cambiar colores y agregar sugerencias.|



