---
title: Establecer el proceso actual | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0baea39c341e8034ff222de32548d0518f115e82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246667"
---
# <a name="set-current-process"></a>Establecer el proceso actual
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Establece el proceso especificado como el proceso activo en el depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>Argumentos  
 `index`  
 Requerido. Índice del proceso.  
  
## <a name="remarks"></a>Comentarios  
 Puede asociar varios procesos mientras realiza la depuración, pero solo hay un proceso activo en el depurador en un momento determinado. Puede utilizar el comando `SetCurrentProcess` para establecer el proceso activo.  
  
## <a name="example"></a>Ejemplo  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



