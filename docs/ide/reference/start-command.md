---
title: Iniciar (Comando)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbd2d64d8103afe1e303052c9b27fc2cc85cab58
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704699"
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
- [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)