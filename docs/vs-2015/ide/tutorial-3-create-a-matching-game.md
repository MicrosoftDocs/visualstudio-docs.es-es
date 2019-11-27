---
title: 'Tutorial 3: Crear un juego de formar parejas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 30ee029fe231202c821c8448d3594192b5ebfdf8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299856"
---
# <a name="tutorial-3-create-a-matching-game"></a>Tutorial 3: Crear un juego de formar parejas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial, compilará un juego de formar parejas en el que el jugador debe buscar las coincidencias entre pares de iconos ocultos. Aprenderá a:

- Almacenar objetos, como iconos, en un objeto `List`.

- Usar un bucle `foreach` en Visual C# o un bucle de `For Each` en Visual Basic para recorrer en iteración los elementos de una lista.

- Realizar un seguimiento del estado de un formulario mediante variables de referencia.

- Crear un controlador de eventos que responda a eventos que se puedan usar con varios objetos.

- Crear un temporizador para la cuenta atrás y desencadenar un evento una y solo una vez después de iniciarse.

  Cuando termine este tutorial, el programa se parecerá al de la ilustración siguiente.

  ![Juego que creará en este tutorial](../ide/media/express-finishedgame.png "Express_FinishedGame") Juego que creará en este tutorial

> [!NOTE]
> En este tutorial, se trata tanto Visual C# como Visual Basic, por lo que deberá centrarse en la información específica del lenguaje de programación que use.

 Si se bloquea o tiene preguntas de programación, envíe la pregunta a uno de los Foros de MSDN. Consulte el [Foro de Visual Basic](https://social.msdn.microsoft.com/Forums/en-US/home) y el [Foro de Visual C#](https://social.msdn.microsoft.com/Forums/en-US/home). Además, dispone de excelentes recursos de aprendizaje en vídeo gratuitos. Para obtener más información sobre la programación en Visual Basic, consulte [Visual Basic Fundamentals: Development for Absolute Beginners](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) (Fundamentos de Visual Basic: desarrollo para principiantes). Para obtener más información sobre la programación en Visual C#, consulte [C# Fundamentals: Development for Absolute Beginners](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) (Fundamentos de C#: desarrollo para principiantes).

## <a name="related-topics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Paso 1: Crear un proyecto y agregar una tabla a un formulario](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Para empezar, cree el proyecto y agregue un control `TableLayoutPanel` para mantener los controles correctamente alineados.|
|[Paso 2: Agregar un objeto aleatorio y una lista de iconos](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Agregará un objeto `Random` y un objeto `List`, para crear una lista de iconos.|
|[Paso 3: Asignar un icono aleatorio a cada etiqueta](../ide/step-3-assign-a-random-icon-to-each-label.md)|Asigne los iconos aleatoriamente a los controles `Label`, de modo que cada juego sea diferente.|
|[Paso 4: Agregar un controlador de eventos Click a cada etiqueta](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Agregará un controlador de eventos Click que cambiará el color de la etiqueta en la que se haga clic.|
|[Paso 5: Agregar referencias a etiquetas](../ide/step-5-add-label-references.md)|Agregará variables de referencia para realizar el seguimiento de las etiquetas en las que se hace clic.|
|[Paso 6: Agregar un temporizador](../ide/step-6-add-a-timer.md)|Agregará un temporizador al formulario para realizar un seguimiento del tiempo que ha transcurrido en el juego.|
|[Paso 7: Mantener visibles los pares](../ide/step-7-keep-pairs-visible.md)|Mantendrá los pares de iconos visibles si se selecciona una pareja coincidente.|
|[Paso 8: Agregar un método para comprobar si el jugador ganó](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Agregará un método `CheckForWinner()` para comprobar si el jugador ganó.|
|[Paso 9: Probar otras características](../ide/step-9-try-other-features.md)|Probará otras características, como cambiar los iconos y colores, agregar una cuadrícula y agregar sonidos. Intentará aumentar el tamaño del tablero y ajustar el temporizador.|
