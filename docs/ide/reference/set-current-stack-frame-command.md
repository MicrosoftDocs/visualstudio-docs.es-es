---
title: Establecer marco de pila actual (Comando)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24880f997d604d3db11ae19a6220c2789da7648f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926071"
---
# <a name="set-current-stack-frame-command"></a>Establecer marco de pila actual (Comando)
Le permite establecer un marco de pila determinado.

## <a name="syntax"></a>Sintaxis

```cmd
Debug.SetCurrentStackFrame index
```

## <a name="arguments"></a>Argumentos
`index`

Obligatorio. Selecciona un marco de pila por su índice.

## <a name="example"></a>Ejemplo

```cmd
>Debug.SetCurrentStackFrame 1
```

## <a name="see-also"></a>Otras referencias

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)