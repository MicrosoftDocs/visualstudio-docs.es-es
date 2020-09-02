---
title: Alias (Comando) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6da744b0db9e41cd1e5039a1bd0d5c93bc4c734a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651689"
---
# <a name="alias-command"></a>Alias (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Crea un nuevo alias para un comando completo, un comando completo con argumentos u otro alias.

> [!TIP]
> Si se escribe `>alias` sin argumentos, se muestra la lista actual de alias y sus definiciones.

## <a name="syntax"></a>Sintaxis

```
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Argumentos
 `aliasname` Opcional. Nombre del nuevo alias. Si no se proporciona ningún valor para `aliasname`, aparece una lista de los alias actuales y sus definiciones.

 `aliasstring` Opcional. Nombre de comando completo o alias existente y cualquier parámetro que desee crear como alias. Si no se proporciona ningún valor para `aliasstring`, se muestran el nombre y la cadena de alias del alias especificado.

## <a name="switches"></a>Modificadores
 /delete o /del o /d Opcional. Elimina el alias especificado, quitándolo de la finalización automática.

 /reset Opcional. Restablece la lista de alias predefinidos a su configuración original. Es decir, restaura todos los alias predefinidos y quita todos los alias definidos por el usuario.

## <a name="remarks"></a>Observaciones
 Puesto que los alias representan comandos, tienen que estar situados al principio de la línea de comandos.

 Cuando se emite este comando, se deben incluir los modificadores inmediatamente detrás del comando, no detrás de los alias, pues de lo contrario el propio modificador se incluye como parte de la cadena de alias.

 El modificador `/reset` pide confirmación antes de que se restauren los alias. No hay ninguna forma abreviada de `/reset`.

## <a name="examples"></a>Ejemplos
 En este ejemplo se crea un nuevo alias, `upper`, para todo el comando Edit.MakeUpperCase.

```
>Tools.Alias upper Edit.MakeUpperCase
```

 En este ejemplo se elimina el alias, `upper`.

```
>Tools.alias /delete upper
```

 Este ejemplo muestra una lista de todos los alias actuales y sus definiciones.

```
>Tools.Alias
```

## <a name="see-also"></a>Consulte también
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md) [ventana comandos](../../ide/reference/command-window.md) [Buscar/comando cuadro](../../ide/find-command-box.md) de comandos de [Visual Studio alias de comandos](../../ide/reference/visual-studio-command-aliases.md)
