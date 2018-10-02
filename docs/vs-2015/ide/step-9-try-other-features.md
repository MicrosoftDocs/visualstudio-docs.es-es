---
title: 'Paso 9: Probar otras características | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 30ce78a2c045ae1d0968605079ab4fd0548e9d14
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577863"
---
# <a name="step-9-try-other-features"></a>Paso 9: Probar otras características
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [paso 9: probar otras características](https://docs.microsoft.com/visualstudio/ide/step-9-try-other-features).  
  
Para aprender más, pruebe a cambiar los iconos y los colores, y agregue un temporizador de juego y sonidos. Para que el juego sea más desafiante, pruebe a aumentar el tamaño del tablero y a ajustar el temporizador.  
  
 Para descargar una versión completa del ejemplo, consulte [Complete Matching Game tutorial sample](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba) (Ejemplo del tutorial Crear un juego de formar parejas).  
  
### <a name="to-try-other-features"></a>Para probar otras características  
  
-   Reemplace los iconos y colores con los que prefiera.  
  
    > [!TIP]
    >  Observe la propiedad [Forecolor](http://msdn.microsoft.com/library/system.windows.forms.control.forecolor%28v=vs.110%29.aspx) de la etiqueta.  
  
-   Agregue un temporizador de juego que mida el tiempo que necesita el jugador para ganar.  
  
    > [!TIP]
    >  Para ello, agregue una etiqueta que muestre el tiempo transcurrido en el formulario sobre TableLayoutPanel, y agregue otro temporizador al formulario que mida el tiempo. Utilice el código para iniciar el temporizador cuando el jugador inicie el juego, y detenga el temporizador después de que coincidan los dos iconos.  
  
-   Agregue un sonido para cuando el jugador encuentre una coincidencia, otro sonido para cuando destape dos iconos que no coincidan y un tercer sonido para cuando el programa vuelva a ocultar los iconos.  
  
    > [!TIP]
    >  Para reproducir sonido, use el espacio de nombres System.media. Consulte [Play Sounds in Windows Forms App (C# .NET)](http://youtu.be/qOh4ooHg1UU) [Reproducir sonidos en la aplicación de Windows Forms (C# .NET)] o [How To Play Audio In Visual Basic](http://youtu.be/-4oPDeQrtMs) (Cómo reproducir audio en Visual Basic) para obtener más información.  
  
-   Aumente el tamaño del tablero para complicar más el juego.  
  
    > [!TIP]
    >  Necesitará hacer algo más que agregar filas y columnas a TableLayoutPanel: también deberá tener en cuenta el número de iconos que cree.  
  
-   Para que el juego sea más desafiante, oculte el primer icono si el jugador es demasiado lento al reaccionar y no elige el segundo icono antes de que pase una cantidad de tiempo concreta.  
  
### <a name="to-continue-or-review"></a>Para continuar o revisar  
  
-   Si se bloquea o tiene preguntas de programación, envíe la pregunta a uno de los Foros de MSDN. Consulte el [Foro de Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) y el [Foro de Visual C#](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral).  
  
-   Dispone de excelentes recursos de aprendizaje en vídeo gratuitos. Para obtener más información sobre la programación en Visual Basic, consulte [Visual Basic Fundamentals: Development for Absolute Beginners](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) (Fundamentos de Visual Basic: desarrollo para principiantes). Para obtener más información sobre la programación en Visual C#, consulte [C# Fundamentals: Development for Absolute Beginners](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) (Fundamentos de C#: desarrollo para principiantes).  
  
-   Para volver al paso anterior del tutorial, consulte [Paso 8: Agregar un método para comprobar si el jugador ganó](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).



