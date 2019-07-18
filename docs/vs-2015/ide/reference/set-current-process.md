---
title: Establecer el proceso actual | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ed19c5b95351f8e9c34255a915fc6a446800f761
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163339"
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
 Obligatorio. Índice del proceso.  
  
## <a name="remarks"></a>Comentarios  
 Puede asociar varios procesos mientras realiza la depuración, pero solo hay un proceso activo en el depurador en un momento determinado. Puede utilizar el comando `SetCurrentProcess` para establecer el proceso activo.  
  
## <a name="example"></a>Ejemplo  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>Otras referencias  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
