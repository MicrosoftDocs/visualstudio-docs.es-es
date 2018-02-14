---
title: "IntelliSense para código de R en Visual Studio | Microsoft Docs"
description: "IntelliSense de Visual Studio muestra información sobre las funciones, los miembros de objeto, los fragmentos de código y las finalizaciones mientras se escribe código de R."
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: de74bd82efc3a0ecc07d31fc830ffabb1d45093c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="intellisense"></a>IntelliSense

Visual Studio IntelliSense muestra información sobre las funciones que puede llamar, miembros de objetos, argumentos de función y [fragmentos de código](code-snippets-for-r.md) directamente en su vista al escribir código. También muestra posibles finalizaciones mientras escribe y las completa al presionar las teclas Tab o Entrar (consulte [Opciones del editor](editing-r-code-in-visual-studio.md#editor-options) de la pestaña **Avanzadas**). IntelliSense está disponible en el editor y en la [ventana interactiva](interactive-repl-for-r-in-visual-studio.md).

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
