---
title: Establecer el proceso actual
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d8c313eebc8623156dd7a575060397ee6e16a9d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748638"
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