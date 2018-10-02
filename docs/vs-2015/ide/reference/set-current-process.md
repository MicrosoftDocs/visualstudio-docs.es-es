---
title: Establecer el proceso actual | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 5281d1c0d926d8d6acdedf323649216c74a4cab9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576531"
---
# <a name="set-current-process"></a>Establecer el proceso actual
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [proceso actual establecido](https://docs.microsoft.com/visualstudio/ide/reference/set-current-process).  
  
  
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
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



