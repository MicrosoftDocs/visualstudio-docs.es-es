---
title: Alias (Comando) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f9fb6a4da0b18cf022ee388ff4a6fa5f399dc650
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49258523"
---
# <a name="alias-command"></a>Alias (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Crea un nuevo alias para un comando completo, un comando completo con argumentos u otro alias.  
  
> [!TIP]
>  Si se escribe `>alias` sin argumentos, se muestra la lista actual de alias y sus definiciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]  
```  
  
## <a name="arguments"></a>Argumentos  
 `aliasname`  
 Opcional. Nombre del nuevo alias. Si no se proporciona ningún valor para `aliasname`, aparece una lista de los alias actuales y sus definiciones.  
  
 `aliasstring`  
 Opcional. Nombre de comando completo o alias existente y cualquier parámetro que desee crear como alias. Si no se proporciona ningún valor para `aliasstring`, se muestran el nombre y la cadena de alias del alias especificado.  
  
## <a name="switches"></a>Modificadores  
 /delete o /del o /d  
 Opcional. Elimina el alias especificado, quitándolo de la finalización automática.  
  
 /reset  
 Opcional. Restablece la lista de alias predefinidos a su configuración original. Es decir, restaura todos los alias predefinidos y quita todos los alias definidos por el usuario.  
  
## <a name="remarks"></a>Comentarios  
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
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



