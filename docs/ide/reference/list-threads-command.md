---
title: Comando Mostrar subprocesos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fa71ec1c6eb8ac50d957782dda02a2c3fb59a3c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="list-threads-command"></a>Mostrar subprocesos (Comando)
Muestra una lista de los subprocesos del programa actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.ListThreads [index]  
```  
  
## <a name="arguments"></a>Argumentos  
 `index`  
 Opcional. Selecciona un subproceso por su índice para que sea el subproceso actual.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se especifica, el argumento `index` marca el subproceso indicado como el subproceso actual. Se muestra un asterisco (*) en la lista junto al subproceso actual.  
  
## <a name="example"></a>Ejemplo  
  
```  
>Debug.ListThreads   
```  
  
## <a name="see-also"></a>Vea también  
 [Comando Mostrar pila de llamadas](../../ide/reference/list-call-stack-command.md)   
 [Comando Mostrar desensamblador](../../ide/reference/list-disassembly-command.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)