---
title: Alias (Comando)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41bddec00866f7c10140abc40c5ff12c623310d3
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33703410"
---
# <a name="alias-command"></a>Alias (Comando)
Crea un nuevo alias para un comando completo, un comando completo con argumentos u otro alias.

> [!TIP]
> Si se escribe `>alias` sin argumentos, se muestra la lista actual de alias y sus definiciones.


## <a name="syntax"></a>Sintaxis

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Argumentos
 `aliasname` Opcional. Nombre del nuevo alias. Si no se proporciona ningún valor para `aliasname`, aparece una lista de los alias actuales y sus definiciones.

 `aliasstring` Opcional. Nombre de comando completo o alias existente y cualquier parámetro que desee crear como alias. Si no se proporciona ningún valor para `aliasstring`, se muestran el nombre y la cadena de alias del alias especificado.

## <a name="switches"></a>Modificadores
 /delete o /del o /d Opcional. Elimina el alias especificado, quitándolo de la finalización automática.

 /reset Opcional. Restablece la lista de alias predefinidos a su configuración original. Es decir, restaura todos los alias predefinidos y quita todos los alias definidos por el usuario.

## <a name="remarks"></a>Comentarios
 Puesto que los alias representan comandos, tienen que estar situados al principio de la línea de comandos.

 Cuando se emite este comando, se deben incluir los modificadores inmediatamente detrás del comando, no detrás de los alias, pues de lo contrario el propio modificador se incluye como parte de la cadena de alias.

 El modificador `/reset` pide confirmación antes de que se restauren los alias. No hay ninguna forma abreviada de `/reset`.

## <a name="examples"></a>Ejemplos
 En este ejemplo se crea un nuevo alias, `upper`, para todo el comando Edit.MakeUpperCase.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

 En este ejemplo se elimina el alias, `upper`.

```cmd
>Tools.alias /delete upper
```

 Este ejemplo muestra una lista de todos los alias actuales y sus definiciones.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Ventana Comandos](../../ide/reference/command-window.md)
- [Cuadro Buscar/Comando](../../ide/find-command-box.md)
- [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)