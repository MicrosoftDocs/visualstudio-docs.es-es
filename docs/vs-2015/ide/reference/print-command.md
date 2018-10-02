---
title: Imprimir (Comando) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e518b3c6ffc3520b408e7c1bfb1fd1703e40a8de
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574613"
---
# <a name="print-command"></a>Imprimir (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [comando Print](https://docs.microsoft.com/visualstudio/ide/reference/print-command).  
  
  
Evalúa una expresión o muestra el texto especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.Print text  
```  
  
## <a name="arguments"></a>Argumentos  
 `text`  
 Requerido. La expresión para evaluar o el texto para mostrar.  
  
## <a name="remarks"></a>Comentarios  
 Puede usar el signo de interrogación (?) como un alias para este comando. Por lo tanto, por ejemplo, el comando  
  
```  
>Debug.Print expA  
```  
  
 también se puede escribir  
  
```  
>? expA  
```  
  
 Ambas versiones de este comando devolverán el valor actual de la expresión `expA`.  
  
## <a name="example"></a>Ejemplo  
  
```  
>Debug.Print varA  
```  
  
## <a name="see-also"></a>Vea también  
 [Evaluar instrucción (Comando)](../../ide/reference/evaluate-statement-command.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



