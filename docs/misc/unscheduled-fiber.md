---
title: "Fibra sin programar | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30948"
  - "vbc30948"
helpviewer_keywords: 
  - "BC30948"
ms.assetid: 982bf6d2-ce62-4451-8a23-82dacf8ee100
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fibra sin programar
El depurador no puede evaluar una expresión porque está en una fibra lógica no programada en un subproceso físico. Esto puede ocurrir si el proceso se ejecuta en un servidor SQL mediante fibras.  
  
 Una fibra consta de una pila y un contexto de registro y se puede ejecutar en cualquier subproceso. Se puede extraer una fibra de un subproceso y después reiniciarla en otro subproceso.  
  
 **Identificador de error:** BC30948  
  
### Para corregir este error  
  
-   Asegúrese de que la fibra está programada en un subproceso físico.  
  
## Vea también  
 [Debugging SQL](http://msdn.microsoft.com/es-es/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)