---
title: Comando Alternar punto de interrupción | Microsoft Docs
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
ms.openlocfilehash: f993d9a0377531b155301bed235c00bf8e6667c4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223163"
---
# <a name="toggle-breakpoint-command"></a>Alternar puntos de interrupción (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



