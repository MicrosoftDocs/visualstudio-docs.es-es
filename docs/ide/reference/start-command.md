---
title: Iniciar (Comando)
description: Obtenga información sobre el comando Iniciar y cómo inicia la depuración del proyecto de inicio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6d9e1e36a2790fb63f9d39c0c83d67d889cc0a8
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616426"
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

## <a name="see-also"></a>Consulte también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
