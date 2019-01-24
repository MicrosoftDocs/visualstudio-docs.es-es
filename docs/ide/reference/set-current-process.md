---
title: Establecer el proceso actual
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c01c399dc76d1b328443edef27edd9a921b1b9c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855288"
---
# <a name="set-current-process"></a>Establecer el proceso actual
Establece el proceso especificado como el proceso activo en el depurador.

## <a name="syntax"></a>Sintaxis

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argumentos
 `index`

 Obligatorio. Índice del proceso.

## <a name="remarks"></a>Comentarios
 Puede asociar varios procesos mientras realiza la depuración, pero solo hay un proceso activo en el depurador en un momento determinado. Puede utilizar el comando `SetCurrentProcess` para establecer el proceso activo.

## <a name="example"></a>Ejemplo

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)