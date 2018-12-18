---
title: Iniciar (Comando) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3b2f482fb33664796a4e6fe451a6a2917e9592f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247722"
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



