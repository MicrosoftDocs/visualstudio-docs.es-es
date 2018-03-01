---
title: Iniciar (Comando) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8eb0efae140613c6caa7bd71d72e0ce4cda37db8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="start-command"></a>Iniciar (Comando)
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
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)