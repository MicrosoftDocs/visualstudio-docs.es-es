---
title: "IntelliSense para código de R en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3677-e5ec-4e11-82a8-d914a93b1aa9
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 4e96184aa9a7711a7c046eb886049563dd308433
ms.contentlocale: es-es
ms.lasthandoff: 07/12/2017

---

# <a name="intellisense"></a>IntelliSense

Visual Studio IntelliSense muestra información sobre las funciones que puede llamar, miembros de objetos, argumentos de función y [fragmentos de código](code-snippets.md) directamente en su vista al escribir código. También muestra posibles finalizaciones mientras escribe y las completa al presionar las teclas Tab o Entrar (consulte [Opciones del editor](code-editing.md#editor-options) de la pestaña **Avanzadas**). IntelliSense está disponible en el editor y en la [ventana interactiva](interactive-repl.md).

![IntelliSense muestra una signatura de función](media/intellisense-function-signature.png) 

Al escribir una función o cualquier otra instrucción, IntelliSense proporciona un menú de finalización automática (que distingue mayúsculas de minúsculas) filtrado por lo que ya ha escrito:

![Menú de finalización automática de IntelliSense](media/intellisense-auto-complete-menu.png)

Si presiona Tab (o bien Entrar o la barra espaciadora, según cómo estén configuradas las opciones), se inserta el elemento seleccionado en la lista desplegable. Puede cambiar la selección con las teclas de dirección. 

IntelliSense también proporciona sugerencias para miembros de objetos de R:
 
![Sugerencias de IntelliSense para miembros de objeto](media/intellisense-auto-complete-r-objects.png)
 
Si presiona ESC, se descarta el menú. Puede hacer que vuelva a aparecer con Ctrl+Barra espaciadora.

Si escribe el `(` de apertura de una llamada de función, se inserta el `)` de cierre y se muestra la ayuda de signatura como se ha mostrado anteriormente:

![Ayuda de signatura de IntelliSense para una función](media/intellisense-function-signature.png)

De nuevo, al presionar ESC se cierra la ventana emergente; para signaturas de función, puede hacer que aparezca de nuevo con Ctrl+Mayús+Barra espaciadora.

> [!Tip]
> Si la ayuda de parámetro oculta el texto que se encuentra debajo, mantenga presionada la tecla Ctrl para hacer que el texto de la ayuda de parámetro sea translúcido.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>IntelliSense para variables y funciones definidas por el usuario

IntelliSense se aplica a funciones definidas por el usuario en el mismo archivo, incluida la finalización del nombre de parámetro:

![IntelliSense para funciones definidas por el usuario](media/intellisense-same-file-functions.png)

![Finalización de parámetro de IntelliSense para funciones definidas por el usuario](media/intellisense-parameter-completion.png)

IntelliSense también se aplica a variables en el mismo archivo y en la sesión actual:

![Finalización de variables de IntelliSense](media/intellisense-variable-completion.png)

> [!Note]
> En la ventana interactiva, IntelliSense analiza solo nombres de la sesión actual de R y omite los archivos del proyecto.

## <a name="code-suggestions"></a>Sugerencias de código

Cuando aparece una bombilla (denominada etiqueta inteligente) en el margen, Visual Studio sugiere que hay disponible un acceso directo para una acción de uso frecuente. Por ejemplo, mantenga el puntero sobre una línea que contenga la instrucción `library` en el editor para ver una bombilla. Si selecciona la bombilla, se muestran las opciones disponibles:

![Etiquetas inteligentes para R en el editor](media/intellisense-smart-tags.png)

