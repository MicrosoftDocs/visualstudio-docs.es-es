---
title: Establecer el proceso actual
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
ms.openlocfilehash: 907ef900283cb3f15d9e65f7196c3cf42e191ed3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="set-current-process"></a>Establecer el proceso actual
Establece el proceso especificado como el proceso activo en el depurador.

## <a name="syntax"></a>Sintaxis

```
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argumentos
 `index`

 Obligatorio. Índice del proceso.

## <a name="remarks"></a>Comentarios
 Puede asociar varios procesos mientras realiza la depuración, pero solo hay un proceso activo en el depurador en un momento determinado. Puede utilizar el comando `SetCurrentProcess` para establecer el proceso activo.

## <a name="example"></a>Ejemplo

```
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)