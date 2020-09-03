---
title: 'Paso 9: Probar otras características | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 379fc9c28b8d36f7bd606719a443b16108f0095d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299982"
---
# <a name="step-9-try-other-features"></a>Paso 9: Probar otras características
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para aprender más, pruebe a cambiar los iconos y los colores, y agregue un temporizador de juego y sonidos. Para que el juego sea más desafiante, pruebe a aumentar el tamaño del tablero y a ajustar el temporizador.

### <a name="to-try-other-features"></a>Para probar otras características

- Reemplace los iconos y colores con los que prefiera.

    > [!TIP]
    > Observe la propiedad [Forecolor](https://msdn.microsoft.com/library/system.windows.forms.control.forecolor%28v=vs.110%29.aspx) de la etiqueta.

- Agregue un temporizador de juego que mida el tiempo que necesita el jugador para ganar.

    > [!TIP]
    > Para ello, agregue una etiqueta que muestre el tiempo transcurrido en el formulario sobre TableLayoutPanel, y agregue otro temporizador al formulario que mida el tiempo. Utilice el código para iniciar el temporizador cuando el jugador inicie el juego, y detenga el temporizador después de que coincidan los dos iconos.

- Agregue un sonido para cuando el jugador encuentre una coincidencia, otro sonido para cuando destape dos iconos que no coincidan y un tercer sonido para cuando el programa vuelva a ocultar los iconos.

    > [!TIP]
    > Para reproducir sonido, use el espacio de nombres System.media. Consulte [Play Sounds in Windows Forms App (C# .NET)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) [Reproducir sonidos en la aplicación de Windows Forms (C# .NET)] o [How To Play Audio In Visual Basic](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be) (Cómo reproducir audio en Visual Basic) para obtener más información.

- Aumente el tamaño del tablero para complicar más el juego.

    > [!TIP]
    > Necesitará hacer algo más que agregar filas y columnas a TableLayoutPanel: también deberá tener en cuenta el número de iconos que cree.

- Para que el juego sea más desafiante, oculte el primer icono si el jugador es demasiado lento al reaccionar y no elige el segundo icono antes de que pase una cantidad de tiempo concreta.

### <a name="to-continue-or-review"></a>Para continuar o revisar

- Si se bloquea o tiene preguntas de programación, envíe la pregunta a uno de los Foros de MSDN. Consulte el [Foro de Visual Basic](https://social.msdn.microsoft.com/Forums/en-US/home) y el [Foro de Visual C#](https://social.msdn.microsoft.com/Forums/en-US/home).

- Dispone de excelentes recursos de aprendizaje en vídeo gratuitos. Para obtener más información sobre la programación en Visual Basic, consulte [aspectos básicos de la Visual Basic: desarrollo para principiantes absolutos](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Para obtener más información sobre la programación en Visual C#, consulte [C# Fundamentals: Development for Absolute Beginners](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) (Fundamentos de C#: desarrollo para principiantes).

- Para volver al paso anterior del tutorial, vea [paso 8: agregar un método para comprobar si el jugador ganó](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
