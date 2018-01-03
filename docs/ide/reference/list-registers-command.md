---
title: Comando Mostrar registros | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 016de257d1ce4e6d2aa95284adbe762a5c54eacf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="list-registers-command"></a>Mostrar registros (Comando)
Muestra el valor de los registros seleccionados y permite modificar la lista de registros que se van a mostrar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
  
## <a name="remarks"></a>Comentarios  
 El alias `r` se puede usar en lugar de `Debug.ListRegisters`.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se usa el alias `r` de `Debug.ListRegisters` para mostrar los valores del grupo de registros `Flags`.  
  
```  
r /Display Flags  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fundamentos de la depuración: ventana Registros](../../debugger/debugging-basics-registers-window.md)   
 [Cómo: Usar la ventana Registros](../../debugger/how-to-use-the-registers-window.md)