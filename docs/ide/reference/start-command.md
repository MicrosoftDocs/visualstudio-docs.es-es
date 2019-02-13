---
title: Iniciar (Comando)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f7488353cd4c64b0afca27060c364a1f9ddc6f8
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55912578"
---
# <a name="start-command"></a>Iniciar (Comando)
Empieza a depurar el proyecto de inicio.

## <a name="syntax"></a>Sintaxis

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Argumentos
 `address`

 Opcional. Dirección en la que el programa suspende la ejecución, similar a un punto de interrupción en el código fuente. Este argumento solo es válido en el modo de depuración.

## <a name="remarks"></a>Comentarios
 Cuando se ejecuta, el comando **Iniciar** realiza una operación RunToCursor en la dirección especificada.

## <a name="example"></a>Ejemplo
 En este ejemplo, se inicia al depurador y se pasa por alto cualquier excepción que se produzca.

```cmd
>Debug.Start
```

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)