---
title: Comando Mostrar subprocesos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 90aff3fb3d3cbb596708bde1db8ff171198a5a60
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59669126"
---
# <a name="list-threads-command"></a>Mostrar subprocesos (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 [Mostrar desensamblador (Comando)](../../ide/reference/list-disassembly-command.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
