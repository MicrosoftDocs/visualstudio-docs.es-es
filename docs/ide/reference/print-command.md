---
title: Imprimir (Comando)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2ef4f0c5c6bd5be2820e1f666529fc43fac59763
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
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
- [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)