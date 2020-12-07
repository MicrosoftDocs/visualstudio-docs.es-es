---
title: Inspección rápida (Comando)
description: Obtenga información sobre el comando Inspección rápida y cómo muestra el texto seleccionado o especificado en el campo Expresión de la ventana Inspección rápida.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6185418364e8b22e1f473308b2db9899c8778d13
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304168"
---
# <a name="quick-watch-command"></a>Inspección rápida (Comando)
Muestra el texto seleccionado o especificado en el campo Expresión de la ventana [Inspección rápida](../../debugger/watch-and-quickwatch-windows.md). Puede usar este cuadro de diálogo para calcular el valor actual de una variable o expresión reconocida por el depurador, o el contenido de un registro. Además, puede cambiar el valor de cualquier variable no constante o el contenido de cualquier registro.

## <a name="syntax"></a>Sintaxis

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Argumentos

`text`\
Opcional. El texto que se va a agregar al cuadro de diálogo **InspecciónRápida**.

## <a name="remarks"></a>Comentarios

Si `text` se omite, el texto seleccionado actualmente o la palabra en el cursor se agrega a la ventana Inspección.

## <a name="example"></a>Ejemplo

```cmd
>Debug.QuickWatch
```

## <a name="see-also"></a>Consulte también

- [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio](../../debugger/watch-and-quickwatch-windows.md) (Establecimiento de una ventana Inspección en variables que usan las ventanas Inspección e Inspección rápida en Visual Studio).
- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
