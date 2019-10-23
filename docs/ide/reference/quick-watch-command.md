---
title: Inspección rápida (Comando)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1de6841f25bcc6f6c45bde93fdd4cf2cb49481ab
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747803"
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

## <a name="see-also"></a>Vea también

- [Establece una inspección en Variables mediante la inspección y las ventanas de inspección rápida en Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)