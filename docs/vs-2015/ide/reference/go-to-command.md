---
title: Comando Ir a | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 454b51b6939a78cdaab8d29f51d30910024adbe3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661199"
---
# <a name="go-to-command"></a>Ir a (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mueve el cursor a la línea especificada.

## <a name="syntax"></a>Sintaxis

```
Edit.GoTo [linenumber]
```

## <a name="arguments"></a>Argumentos
 `linenumber` Opcional. Entero que representa el número de la línea a la que se debe ir.

## <a name="remarks"></a>Observaciones
 La numeración de líneas empieza por el uno. Si el valor de `linenumber` es menor que uno, se muestra la primera línea. Si el valor de `linenumber` es mayor que el número de la última línea, se muestra la última línea.

 Si no se especifica ningún valor para `linenumber`, se muestra el cuadro de diálogo **Ir a la línea**.

 El alias de este comando es GoToLn.

## <a name="example"></a>Ejemplo

```
>Edit.GoTo 125
```

## <a name="see-also"></a>Consulte también
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md) [ventana comandos](../../ide/reference/command-window.md) [Buscar/comando cuadro](../../ide/find-command-box.md) de comandos de [Visual Studio alias de comandos](../../ide/reference/visual-studio-command-aliases.md)
