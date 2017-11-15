---
title: Establecer el proceso actual | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6bd4ab27a36e37e31ec348b80327b6046c5ecbd3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="set-current-process"></a>Establecer el proceso actual
Establece el proceso especificado como el proceso activo en el depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>Argumentos  
 `index`  
 Obligatorio. Índice del proceso.  
  
## <a name="remarks"></a>Comentarios  
 Puede asociar varios procesos mientras realiza la depuración, pero solo hay un proceso activo en el depurador en un momento determinado. Puede utilizar el comando `SetCurrentProcess` para establecer el proceso activo.  
  
## <a name="example"></a>Ejemplo  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)