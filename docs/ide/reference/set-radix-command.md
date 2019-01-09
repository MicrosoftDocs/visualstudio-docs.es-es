---
title: Establecer base (Comando)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.setradix
helpviewer_keywords:
- Set Radix command
- Debug.SetRadix command
ms.assetid: 6ffd1554-7530-4da4-b5f5-e276a5034f3b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93172b8ed16e2520c060671d12ef0ab35960f6ad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53829413"
---
# <a name="set-radix-command"></a>Establecer base (Comando)
Establece o devuelve la base numérica que se ha usado para mostrar valores enteros.

## <a name="syntax"></a>Sintaxis

```cmd
Debug.SetRadix [10 | 16 | hex | dec]
```

## <a name="arguments"></a>Argumentos
 `10` o `16` o `hex` o `dec`

 Opcional. Indica decimal (10 o dec) o hexadecimal (16 o hex). Si se omite un argumento, se devuelve el valor base actual.

## <a name="example"></a>Ejemplo
 En este ejemplo se establece el entorno para mostrar valores enteros en formato hexadecimal.

```cmd
>Debug.SetRadix hex
```

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)