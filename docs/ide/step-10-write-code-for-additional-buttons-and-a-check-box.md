---
title: 'Paso 10: Escribir código para botones adicionales y una casilla | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-acquisition
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13461522bd4e195eec5bc2a681c8c6b1a9def5d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Paso 10: Escribir código para botones adicionales y una casilla
Ahora, está listo para completar los otros cuatro métodos. Podría copiar y pegar este código, pero si desea aprender lo máximo con este tutorial, escriba el código y utilice IntelliSense.  
  
 Este código agrega funcionalidad a los botones que agregó anteriormente. Sin este código, los botones no hacen nada. Los botones utilizan el código de sus eventos `Click` (y la casilla utiliza el evento `CheckChanged`) para realizar diferentes operaciones cuando se activan los controles. Por ejemplo, el evento `clearButton_Click`, que se activa al pulsar el botón **Borrar la imagen**, borra la imagen actual y establece su propiedad `Image` en `null` (o `nothing`). Cada evento del código incluye comentarios que explican lo que hace el código.  
  
 ![vínculo al vídeo](../data-tools/media/playvideo.gif "PlayVideo")Para obtener una versión en vídeo de este tema, vea el [Tutorial 1: Crear un visor de imágenes en Visual Basic (vídeo 5)](http://go.microsoft.com/fwlink/?LinkId=205216) o el [Tutorial 1: Crear un visor de imágenes en C# (vídeo 5)](http://go.microsoft.com/fwlink/?LinkId=205206). En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio.  
  
> [!NOTE]
>  El procedimiento recomendado es comentar siempre el código. Los comentarios son información que leerán otras personas y merece la pena dedicar tiempo a hacer que el código resulte fácil de entender. El programa pasa por alto todo lo que hay en una línea de comentario. En Visual C#, para marcar una línea como comentario se escriben dos barras diagonales (//) al principio. En Visual Basic, se utiliza para ello una comilla sencilla (').  
  
### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Si desea escribir código para otros adicionales y una casilla  
  
-   Agregue el código siguiente al archivo de código Form1 (Form1.cs o Form1.vb). Pulse la pestaña **VB** para ver el código de Visual Basic.  
  
     [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]
     [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]  
  
### <a name="to-continue-or-review"></a>Para continuar o revisar  
  
-   Para ir al siguiente paso del tutorial, vea [Paso 11: Ejecutar el programa y probar otras características](../ide/step-11-run-your-program-and-try-other-features.md).  
  
-   Para volver al paso anterior del tutorial, vea [Paso 9: Revisar, comentar y probar el código](../ide/step-9-review-comment-and-test-your-code.md).