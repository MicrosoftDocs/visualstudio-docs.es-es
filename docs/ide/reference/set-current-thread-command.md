---
title: Establecer subproceso actual (Comando)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ea652f04295871f9437d80555254caecab87a48
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926062"
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

## <a name="see-also"></a>Otras referencias

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)