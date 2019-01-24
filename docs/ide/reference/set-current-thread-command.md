---
title: Establecer subproceso actual (Comando)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03d253d9be0d8bf5456f1a436d45762d6f030f86
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855343"
---
# <a name="set-current-thread-command"></a>Establecer subproceso actual (Comando)
Establece el subproceso especificado como el subproceso actual.

## <a name="syntax"></a>Sintaxis

```
Debug.SetCurrentThread index
```

## <a name="arguments"></a>Argumentos
 `index`

 Obligatorio. Selecciona un subproceso por su índice.

## <a name="example"></a>Ejemplo

```
>Debug.SetCurrentThread 1
```

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)