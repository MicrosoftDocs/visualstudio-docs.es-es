---
title: Debug.Print
ms.date: 11/04/2016
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
ms.openlocfilehash: df609011250cebc097d3d356242302dbe41f8007
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969090"
---
# <a name="print-command"></a>Imprimir (Comando)

Evalúa una expresión o muestra el texto especificado.

## <a name="syntax"></a>Sintaxis

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Argumentos

`text`

Obligatorio. La expresión para evaluar o el texto para mostrar.

## <a name="remarks"></a>Comentarios

Puede usar el signo de interrogación (?) como un alias para este comando. Por lo tanto, por ejemplo, el comando

```cmd
>Debug.Print expA
```

también se puede escribir como

```cmd
? expA
```

Ambas versiones de este comando devuelven el valor actual de la expresión `expA`.

## <a name="example"></a>Ejemplo

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>Vea también

- [Evaluar instrucción (Comando)](../../ide/reference/evaluate-statement-command.md)
- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)