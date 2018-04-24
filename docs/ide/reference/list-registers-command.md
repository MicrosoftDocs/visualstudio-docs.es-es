---
title: Comando Mostrar registros | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a4bd4dac2cc8faf6d98ee130e0796254035b1ca2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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