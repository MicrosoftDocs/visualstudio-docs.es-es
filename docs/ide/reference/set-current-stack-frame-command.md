---
title: Comando Establecer marco de pila actual | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.setcurrentstackframe
helpviewer_keywords:
- Set Current Stack Frame command
- Debug.SetCurrentStackFrame command
ms.assetid: 3dcf52c0-6781-4598-bac2-0094dce67c20
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bcc24fbcf5089d60dade18cbcb08135951cbc6b9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="set-current-stack-frame-command"></a>Establecer marco de pila actual (Comando)
Le permite establecer un marco de pila determinado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.SetCurrentStackFrame index  
```  
  
## <a name="arguments"></a>Argumentos  
 `index`  
 Obligatorio. Selecciona un marco de pila por su índice.  
  
## <a name="example"></a>Ejemplo  
  
```  
>Debug.SetCurrentStackFrame 1  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)