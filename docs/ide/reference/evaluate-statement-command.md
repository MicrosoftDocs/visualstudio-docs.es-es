---
title: "Evaluar instrucci&#243;n (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.evaluatestatement"
helpviewer_keywords: 
  - "Debug.EvaluateStatement (comando)"
  - "Evaluar instrucción (comando)"
ms.assetid: 032039bc-9477-4f93-9b9d-66d4be0e90f4
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Evaluar instrucci&#243;n (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Evalúa y muestra la instrucción dada.  
  
## Sintaxis  
  
```  
Debug.EvaluateStatement text   
```  
  
## Argumentos  
 `text`  
 Obligatorio.  Instrucción que se va a evaluar.  
  
## Comentarios  
 La ventana utilizada para escribir el comando **EvaluateStatement** determina si un signo igual \(\=\) se interpreta como un operador de comparación o como un operador de asignación.  
  
 En la ventana **Comandos**, un signo igual \(\=\) se interpreta como un operador de comparación.  Así, por ejemplo, si los valores de las variables `a` y `b` son diferentes, el comando  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 devolverá un valor de `false`.  
  
 En la ventana **Inmediato**, por el contrario, un signo igual \(\=\) se interpreta como un operador de asignación.  Así, por ejemplo, el comando  
  
```  
>Debug.EvaluateStatement(a=b)  
```  
  
 asignará a la variable `a` el valor de la variable `b`.  
  
## Ejemplo  
  
```  
>Debug.EvaluateStatement(a+b)  
```  
  
## Vea también  
 [Imprimir \(Comando\)](../../ide/reference/print-command.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)