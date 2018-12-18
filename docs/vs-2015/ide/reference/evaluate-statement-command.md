---
title: Evaluar instrucción (Comando) | Microsoft Docs
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
- debug.evaluatestatement
helpviewer_keywords:
- Debug.EvaluateStatement command
- Evaluate Statement command
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d3e50b519b162201d741f2460a8e9dbbe675c16e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230326"
---
# <a name="evaluate-statement-command"></a>Evaluar instrucción (Comando)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Evalúa y muestra la instrucción dada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Debug.EvaluateStatement text   
```  
  
## <a name="arguments"></a>Argumentos  
 `text`  
 Requerido. Instrucción que se va a evaluar.  
  
## <a name="remarks"></a>Comentarios  
 La ventana que se usa para escribir el comando **EvaluateStatement** determina si el signo igual (=) se interpreta como operador de comparación o como operador de asignación.  
  
 En la ventana **Comandos**, un signo igual (=) se interpreta como un operador de comparación. Por lo tanto, por ejemplo, si los valores de las variables `a` y `b` son diferentes, entonces el comando  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 devolverá un valor de `false`.  
  
 En la ventana **Inmediato**, por el contrario, un signo igual (=) se interpreta como un operador de asignación. Por lo tanto, por ejemplo, el comando  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 asignará a la variable `a` el valor de la variable `b`.  
  
## <a name="example"></a>Ejemplo  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## <a name="see-also"></a>Vea también  
 [Imprimir (Comando)](../../ide/reference/print-command.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana Comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar/Comando](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



