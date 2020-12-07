---
title: Mostrar registros (Comando)
description: Obtenga información sobre el comando Mostrar registros y cómo muestra el valor de los registros seleccionados y le permite modificar la lista de registros que se van a mostrar.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 5459ded60ea90ae00a3f943f829065a82548d160
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305303"
---
# <a name="list-registers-command"></a>Mostrar registros (Comando)
Muestra el valor de los registros seleccionados y permite modificar la lista de registros que se van a mostrar.

## <a name="syntax"></a>Sintaxis

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Conmutadores
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

## <a name="remarks"></a>Comentarios
El alias `r` se puede usar en lugar de `Debug.ListRegisters`.

## <a name="example"></a>Ejemplo
En este ejemplo se usa el alias `r` de `Debug.ListRegisters` para mostrar los valores del grupo de registros `Flags`.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Consulte también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fundamentos de la depuración: Ventana Registros](../../debugger/debugging-basics-registers-window.md)
- [Cómo: Uso de la ventana Registros](../../debugger/how-to-use-the-registers-window.md)
