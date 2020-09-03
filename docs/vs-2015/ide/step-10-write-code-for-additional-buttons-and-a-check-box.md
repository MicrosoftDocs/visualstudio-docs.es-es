---
title: 'Paso 10: Escribir código para botones adicionales y una casilla | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e24152bf2e6acfcb1ed20b75a5c817e0336cdd4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851596"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Paso 10: Escribir código para botones adicionales y una casilla
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ahora, está listo para completar los otros cuatro métodos. Podría copiar y pegar este código, pero si desea aprender lo máximo con este tutorial, escriba el código y utilice IntelliSense.

 Este código agrega funcionalidad a los botones que agregó anteriormente. Sin este código, los botones no hacen nada. Los botones utilizan el código de sus eventos `Click` (y la casilla utiliza el evento `CheckChanged`) para realizar diferentes operaciones cuando se activan los controles. Por ejemplo, el evento `clearButton_Click`, que se activa al pulsar el botón **Borrar la imagen**, borra la imagen actual y establece su propiedad `Image` en `null` (o `nothing`). Cada evento del código incluye comentarios que explican lo que hace el código.

 ![vínculo a vídeo](../data-tools/media/playvideo.gif "PlayVideo") Para obtener una versión en vídeo de este tema, vea el [tutorial 1: crear un visor de imágenes en Visual Basic-vídeo 5 o el](https://msdn.microsoft.com/vbasic/gg315356.aspx) [tutorial 1: crear un visor de imágenes en C# (vídeo 5)](https://msdn.microsoft.com/vcsharp/gg278413.aspx). En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio.

> [!NOTE]
> El procedimiento recomendado es comentar siempre el código. Los comentarios son información que leerán otras personas y merece la pena dedicar tiempo a hacer que el código resulte fácil de entender. El programa pasa por alto todo lo que hay en una línea de comentario. En Visual C#, para marcar una línea como comentario se escriben dos barras diagonales (//) al principio. En Visual Basic, se utiliza para ello una comilla sencilla (').

### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Si desea escribir código para otros adicionales y una casilla

- Agregue el código siguiente al archivo de código Form1 (Form1.cs o Form1.vb). Pulse la pestaña **VB** para ver el código de Visual Basic.

     [!code-csharp[VbExpressTutorial1Step9_10#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step9_10#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#2)]

### <a name="to-continue-or-review"></a>Para continuar o revisar

- Para ir al siguiente paso del tutorial, vea [paso 11: ejecutar el programa y probar otras características](../ide/step-11-run-your-program-and-try-other-features.md).

- Para volver al paso anterior del tutorial, vea [paso 9: revisar, comentar y probar el código](../ide/step-9-review-comment-and-test-your-code.md).
