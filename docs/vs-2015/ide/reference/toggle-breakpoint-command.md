---
title: Comando Alternar punto de interrupción | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 11f0598fa20a5293d662bdbb23b7f67c6c0c80b2
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54793179"
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
