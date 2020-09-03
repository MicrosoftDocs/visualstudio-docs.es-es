---
title: Comando Mostrar subprocesos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc11479901785b19235e0962d3ae90e552e5b33b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671137"
---
# <a name="list-threads-command"></a>Mostrar subprocesos (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Muestra una lista de los subprocesos del programa actual.

## <a name="syntax"></a>Sintaxis

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Argumentos
 `index` Opcional. Selecciona un subproceso por su índice para que sea el subproceso actual.

## <a name="remarks"></a>Observaciones
 Cuando se especifica, el argumento `index` marca el subproceso indicado como el subproceso actual. Se muestra un asterisco (*) en la lista junto al subproceso actual.

## <a name="example"></a>Ejemplo

```
>Debug.ListThreads
```

## <a name="see-also"></a>Consulte también
 Enumerar [lista de](../../ide/reference/list-disassembly-command.md) comandos de la [pila de llamadas](../../ide/reference/list-call-stack-command.md) comandos de Visual Studio comandos de [Visual Studio](../../ide/reference/visual-studio-commands.md) [ventana](../../ide/reference/command-window.md) de comandos [Buscar/comando cuadros](../../ide/find-command-box.md) de comandos de [Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
