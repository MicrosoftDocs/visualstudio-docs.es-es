---
title: Imprimir (Comando)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1677e05668b8681976447ef9ee401624d82bdd9a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54939834"
---
# <a name="print-command"></a>Imprimir (Comando)
Evalúa una expresión o muestra el texto especificado.

## <a name="syntax"></a>Sintaxis

```cmd
Debug.Print text
```

## <a name="arguments"></a>Argumentos
 `text`

 Obligatorio. La expresión para evaluar o el texto para mostrar.

## <a name="remarks"></a>Comentarios
 Puede usar el signo de interrogación (?) como un alias para este comando. Por lo tanto, por ejemplo, el comando

```cmd
>Debug.Print expA
```

 también se puede escribir

```cmd
>? expA
```

 Ambas versiones de este comando devolverán el valor actual de la expresión `expA`.

## <a name="example"></a>Ejemplo

```cmd
>Debug.Print varA
```

## <a name="see-also"></a>Vea también

- [Evaluar instrucción (Comando)](../../ide/reference/evaluate-statement-command.md)
- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)