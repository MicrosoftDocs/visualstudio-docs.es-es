---
title: Inspección (Comando)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ac779dc902a331a45b600113a11db5364293f74
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925948"
---
# <a name="watch-command"></a>Inspección (Comando)
Crea y abre una instancia especificada de una ventana **Inspección** . Puede usar una ventana **Inspección** para calcular los valores de variables, expresiones y registros, para editar estos valores y para guardar los resultados.

## <a name="syntax"></a>Sintaxis

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Argumentos

`index`\
Obligatorio. El número de instancia de la ventana Inspección.

## <a name="remarks"></a>Comentarios

`index` debe ser un entero. Los valores válidos son 1, 2, 3 o 4.

## <a name="example"></a>Ejemplo

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Otras referencias

- [Ventanas de variables locales y automáticas](../../debugger/autos-and-locals-windows.md)
- [Establece una inspección en Variables mediante la inspección y las ventanas de inspección rápida en Visual Studio](../../debugger/watch-and-quickwatch-windows.md)
- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)