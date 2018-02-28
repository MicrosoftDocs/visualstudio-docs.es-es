---
title: Establecer subproceso actual (Comando) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 24a3f7d50d90769fe64b3657a0327eb8c96b7b42
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="set-current-thread-command"></a>Establecer subproceso actual (Comando)
Establece el subproceso especificado como el subproceso actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.SetCurrentThread index  
```  
  
## <a name="arguments"></a>Argumentos  
 `index`  
 Obligatorio. Selecciona un subproceso por su índice.  
  
## <a name="example"></a>Ejemplo  
  
```  
>Debug.SetCurrentThread 1  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)