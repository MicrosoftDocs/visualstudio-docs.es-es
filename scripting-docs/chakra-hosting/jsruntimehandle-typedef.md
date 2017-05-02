---
title: "JsRuntimeHandle (Typedef) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 69e59bfd-9b0e-4710-9aa8-fbd6844171bc
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsRuntimeHandle (Typedef)
Identificador para un runtime de Chakra.  
  
## Sintaxis  
  
```  
typedef void *JsRuntimeHandle;  
```  
  
## Comentarios  
 Cada runtime de Chakra tiene su propio motor de ejecución, compilador JIT y montón de recolección de elementos no utilizados independientes.  Como tal, cada runtime está completamente aislado del resto.  
  
 Los runtime se pueden usar en cualquier subproceso, pero solo un subproceso puede llamar a un runtime en un momento determinado.  
  
> [!WARNING]
>  Al contrario que otras referencias a objetos de la API de hospedaje de Chakra, los elementos no utilizados de un JsRuntimeHandle no se recolectan, puesto que este contiene el propio montón de recolección de elementos no utilizados.  Un runtime seguirá existiendo hasta que se llame a JsDisposeRuntime.  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)