---
title: 'Paso 10: Escribir código para botones adicionales y una casilla de verificación | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 58e50e7d70c485a4a49564ec0a57ba03b74e4a85
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786030"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Paso 10: Escribir código para botones adicionales y una casilla
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ahora, está listo para completar los otros cuatro métodos. Podría copiar y pegar este código, pero si desea aprender lo máximo con este tutorial, escriba el código y utilice IntelliSense.  
  
 Este código agrega funcionalidad a los botones que agregó anteriormente. Sin este código, los botones no hacen nada. Los botones utilizan el código de sus eventos `Click` (y la casilla utiliza el evento `CheckChanged`) para realizar diferentes operaciones cuando se activan los controles. Por ejemplo, el evento `clearButton_Click`, que se activa al pulsar el botón **Borrar la imagen**, borra la imagen actual y establece su propiedad `Image` en `null` (o `nothing`). Cada evento del código incluye comentarios que explican lo que hace el código.  
  
 ![vínculo a vídeo](../data-tools/media/playvideo.gif "PlayVideo")para una versión en vídeo de este tema, consulte [Tutorial 1: crear un visor de imágenes en Visual Basic - vídeo 5](http://go.microsoft.com/fwlink/?LinkId=205216) o [Tutorial 1: crear un visor de imágenes en C#: Vídeo 5](http://go.microsoft.com/fwlink/?LinkId=205206). En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio.  
  
> [!NOTE]
>  El procedimiento recomendado es comentar siempre el código. Los comentarios son información que leerán otras personas y merece la pena dedicar tiempo a hacer que el código resulte fácil de entender. El programa pasa por alto todo lo que hay en una línea de comentario. En Visual C#, para marcar una línea como comentario se escriben dos barras diagonales (//) al principio. En Visual Basic, se utiliza para ello una comilla sencilla (').  
  
### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Si desea escribir código para otros adicionales y una casilla  
  
-   Agregue el código siguiente al archivo de código Form1 (Form1.cs o Form1.vb). Pulse la pestaña **VB** para ver el código de Visual Basic.  
  
     [!code-csharp[VbExpressTutorial1Step9_10#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step9_10#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#2)]  
  
### <a name="to-continue-or-review"></a>Para continuar o revisar  
  
-   Para ir al siguiente paso del tutorial, vea [Paso 11: Ejecutar el programa y probar otras características](../ide/step-11-run-your-program-and-try-other-features.md).  
  
-   Para volver al paso anterior del tutorial, vea [Paso 9: Revisar, comentar y probar el código](../ide/step-9-review-comment-and-test-your-code.md).
