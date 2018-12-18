---
title: Inspección rápida (Comando)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce3c95591809b847141dde07b2a770d9b4597a5f
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33703962"
---
# <a name="quick-watch-command"></a>Inspección rápida (Comando)
Muestra el texto seleccionado o especificado en el campo Expresión de la ventana [Inspección rápida](../../debugger/watch-and-quickwatch-windows.md). Puede usar este cuadro de diálogo para calcular el valor actual de una variable o expresión reconocida por el depurador, o el contenido de un registro. Además, puede cambiar el valor de cualquier variable no constante o el contenido de cualquier registro.

## <a name="syntax"></a>Sintaxis

```cmd
Debug.QuickWatchq [text]
```

## <a name="arguments"></a>Argumentos
 `text`

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
- [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)