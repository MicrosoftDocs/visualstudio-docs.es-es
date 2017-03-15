---
title: "Imprimir (Comando) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "debug.print"
helpviewer_keywords: 
  - "Debug.Print (comando)"
  - "Imprimir (comando)"
  - "Print (método)"
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Imprimir (Comando)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Evalúa una expresión o muestra el texto especificado.  
  
## Sintaxis  
  
```  
Debug.Print text  
```  
  
## Argumentos  
 `text`  
 Obligatorio.  La expresión que se va a evaluar o el texto que se va a mostrar.  
  
## Comentarios  
 Puede utilizar el signo de interrogación \(?\) como un alias para este comando.  Así, por ejemplo, el comando  
  
```  
>Debug.Print expA  
```  
  
 también se puede escribir como  
  
```  
>? expA  
```  
  
 Ambas versiones de este comando devolverán el valor actual de la expresión `expA`.  
  
## Ejemplo  
  
```  
>Debug.Print varA  
```  
  
## Vea también  
 [Evaluar instrucción \(Comando\)](../../ide/reference/evaluate-statement-command.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Ventana de comandos](../../ide/reference/command-window.md)   
 [Cuadro Buscar\/Comando](../../ide/find-command-box.md)   
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)