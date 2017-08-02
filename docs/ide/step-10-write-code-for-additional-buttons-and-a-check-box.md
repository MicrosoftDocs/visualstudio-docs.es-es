---
title: "Paso 10: Escribir código para botones adicionales y una casilla | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
caps.latest.revision: 21
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d89b7cf0a81ed9987f8a09fb6e3139deb13f579e
ms.contentlocale: es-es
ms.lasthandoff: 05/19/2017

---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Paso 10: Escribir código para botones adicionales y una casilla
Ahora, está listo para completar los otros cuatro métodos. Podría copiar y pegar este código, pero si desea aprender lo máximo con este tutorial, escriba el código y utilice IntelliSense.  
  
 Este código agrega funcionalidad a los botones que agregó anteriormente. Sin este código, los botones no hacen nada. Los botones utilizan el código de sus eventos `Click` (y la casilla utiliza el evento `CheckChanged`) para realizar diferentes operaciones cuando se activan los controles. Por ejemplo, el evento `clearButton_Click`, que se activa al pulsar el botón **Borrar la imagen**, borra la imagen actual y establece su propiedad `Image` en `null` (o `nothing`). Cada evento del código incluye comentarios que explican lo que hace el código.  
  
 ![vínculo al vídeo](~/data-tools/media/playvideo.gif "PlayVideo")Para obtener una versión en vídeo de este tema, vea el [Tutorial 1: Crear un visor de imágenes en Visual Basic (vídeo 5)](http://go.microsoft.com/fwlink/?LinkId=205216) o el [Tutorial 1: Crear un visor de imágenes en C# (vídeo 5)](http://go.microsoft.com/fwlink/?LinkId=205206). En estos vídeos se utilizó una versión anterior de Visual Studio, por lo que hay ligeras diferencias en algunos comandos de menú y otros elementos de la interfaz de usuario. Sin embargo, los conceptos y procedimientos funcionan de forma similar en la versión actual de Visual Studio.  
  
> [!NOTE]
>  El procedimiento recomendado es comentar siempre el código. Los comentarios son información que leerán otras personas y merece la pena dedicar tiempo a hacer que el código resulte fácil de entender. El programa pasa por alto todo lo que hay en una línea de comentario. En Visual C#, para marcar una línea como comentario se escriben dos barras diagonales (//) al principio. En Visual Basic, se utiliza para ello una comilla sencilla (').  
  
### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Si desea escribir código para otros adicionales y una casilla  
  
-   Agregue el código siguiente al archivo de código Form1 (Form1.cs o Form1.vb). Pulse la pestaña **VB** para ver el código de Visual Basic.  
  
     [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]  [!code-cs[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]  
  
### <a name="to-continue-or-review"></a>Para continuar o revisar  
  
-   Para ir al siguiente paso del tutorial, vea [Paso 11: Ejecutar el programa y probar otras características](../ide/step-11-run-your-program-and-try-other-features.md).  
  
-   Para volver al paso anterior del tutorial, vea [Paso 9: Revisar, comentar y probar el código](../ide/step-9-review-comment-and-test-your-code.md).
