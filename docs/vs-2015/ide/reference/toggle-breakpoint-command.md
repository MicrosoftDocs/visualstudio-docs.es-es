---
title: Comando Alternar punto de interrupción | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c7dd3bd7a4d42b8135aed034464223af53091f87
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566013"
---
# <a name="toggle-breakpoint-command"></a>Alternar puntos de interrupción (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Alternar punto de interrupción (comando)](https://docs.microsoft.com/visualstudio/ide/reference/toggle-breakpoint-command).  
  
  
Activa o desactiva el punto de interrupción, en función del estado actual, en la ubicación actual del archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## <a name="arguments"></a>Argumentos  
 `text`  
 Opcional. Si se especifica texto, la línea se marca como un punto de interrupción con nombre. En caso contrario, la línea se marca como un punto de interrupción sin nombre, que es similar a lo que sucede cuando se presiona la tecla F9.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se alterna el punto de interrupción actual.  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



