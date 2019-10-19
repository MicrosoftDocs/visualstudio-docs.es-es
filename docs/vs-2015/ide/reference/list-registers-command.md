---
title: Comando Mostrar registros | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3476244d3044eb80dbfce3559479421b012cc5fa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659499"
---
# <a name="list-registers-command"></a>Mostrar registros (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Muestra el valor de los registros seleccionados y permite modificar la lista de registros que se van a mostrar.

## <a name="syntax"></a>Sintaxis

```
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Modificadores
 /Display [{`register`&#124; `registerGroup`}...] Muestra los valores del `register` o `registerGroup` especificados. Si no hay ningún objeto `register` o `registerGroup` especificado, se muestra la lista predeterminada de registros. Si no se especifica ningún modificador, el comportamiento es el mismo. Por ejemplo:

 `Debug.ListRegisters /Display eax`

 es equivalente a

 `Debug.ListRegisters eax`

 /List muestra todos los grupos de registros de la lista.

 /Watch [{`register`&#124; `registerGroup`}...] Agrega uno o más valores de `register` o `registerGroup` a la lista.

 /UNWatch [{`register`&#124; `registerGroup`}...] Quita uno o varios valores `register` o `registerGroup` de la lista.

## <a name="remarks"></a>Comentarios
 El alias `r` se puede usar en lugar de `Debug.ListRegisters`.

## <a name="example"></a>Ejemplo
 En este ejemplo se usa el alias `r` de `Debug.ListRegisters` para mostrar los valores del grupo de registros `Flags`.

```
r /Display Flags
```

## <a name="see-also"></a>Vea también
 Aspectos básicos de la depuración de los [comandos de Visual Studio](../../ide/reference/visual-studio-commands.md) [: ventana registros](../../debugger/debugging-basics-registers-window.md) [Cómo: usar la ventana registros](../../debugger/how-to-use-the-registers-window.md)
