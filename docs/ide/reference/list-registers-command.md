---
title: Mostrar registros (Comando)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e87b10a7827b5365b507abb2c72a21506e59c19e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568690"
---
# <a name="list-registers-command"></a>Mostrar registros (Comando)
Muestra el valor de los registros seleccionados y permite modificar la lista de registros que se van a mostrar.

## <a name="syntax"></a>Sintaxis

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Modificadores
/Display [{`register`&#124;`registerGroup`}...]

Muestra los valores del objeto `register` o `registerGroup` especificado. Si no hay ningún objeto `register` o `registerGroup` especificado, se muestra la lista predeterminada de registros. Si no se especifica ningún modificador, el comportamiento es el mismo. Por ejemplo:

`Debug.ListRegisters /Display eax`

es equivalente a

`Debug.ListRegisters eax`

/List

Muestra todos los grupos de registros de la lista.

/Watch [{`register`&#124;`registerGroup`}...]

Agrega uno o varios valores `register` o `registerGroup` a la lista.

/Unwatch [{`register`&#124;`registerGroup`}...]

Quita uno o varios valores `register` o `registerGroup` de la lista.

## <a name="remarks"></a>Observaciones
El alias `r` se puede usar en lugar de `Debug.ListRegisters`.

## <a name="example"></a>Ejemplo
En este ejemplo se usa el alias `Debug.ListRegisters` de `r` para mostrar los valores del grupo de registros `Flags`.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fundamentos de la depuración: ventana Registros](../../debugger/debugging-basics-registers-window.md)
- [Cómo: Usar la ventana Registros](../../debugger/how-to-use-the-registers-window.md)
