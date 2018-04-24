---
title: Establecer el proceso actual | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ea3028be32fdccffd70f7b3d0aa9d3b4eba172c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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