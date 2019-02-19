---
title: Iniciar (Comando) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f08baa8c27debf6493ca090a2a5e80f02b3da982
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54774460"
---
# <a name="start-command"></a>Iniciar (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Empieza a depurar el proyecto de inicio.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.Start [address]  
```  
  
## <a name="arguments"></a>Argumentos  
 `address`  
 Opcional. Dirección en la que el programa suspende la ejecución, similar a un punto de interrupción en el código fuente. Este argumento solo es válido en el modo de depuración.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se ejecuta, el comando **Iniciar** realiza una operación RunToCursor en la dirección especificada.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, se inicia al depurador y se pasa por alto cualquier excepción que se produzca.  
  
```  
>Debug.Start  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
