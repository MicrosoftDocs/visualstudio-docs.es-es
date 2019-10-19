---
title: Imprimir (Comando) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136edf7fa91e4caeb9303edfd4441ee178fa6038
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662153"
---
# <a name="print-command"></a>Imprimir (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Evalúa una expresión o muestra el texto especificado.

## <a name="syntax"></a>Sintaxis

```
Debug.Print text
```

## <a name="arguments"></a>Argumentos
 `text` Obligatorio. La expresión para evaluar o el texto para mostrar.

## <a name="remarks"></a>Comentarios
 Puede usar el signo de interrogación (?) como un alias para este comando. Por lo tanto, por ejemplo, el comando

```
>Debug.Print expA
```

 también se puede escribir

```
>? expA
```

 Ambas versiones de este comando devolverán el valor actual de la expresión `expA`.

## <a name="example"></a>Ejemplo

```
>Debug.Print varA
```

## <a name="see-also"></a>Otras referencias
 [Comando de la instrucción Evaluate](../../ide/reference/evaluate-statement-command.md) comandos de [Visual Studio](../../ide/reference/visual-studio-commands.md) comandos de la [ventana comandos](../../ide/reference/command-window.md) [Buscar/comando cuadro](../../ide/find-command-box.md) de comandos de [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
