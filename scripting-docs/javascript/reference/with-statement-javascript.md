---
title: "with (Instrucci&#243;n de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "with_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "With (instrucción)"
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# with (Instrucci&#243;n de JavaScript)
Establece el objeto predeterminado para una instrucción.  
  
## Sintaxis  
  
```  
with (object) {  
    statements  
}   
```  
  
## Parámetros  
 `object`  
 Objeto predeterminado.  
  
 `statements`  
 Una o más instrucciones para las que `object` es el objeto predeterminado.  
  
## Comentarios  
 La instrucción `with` se utiliza habitualmente para reducir el volumen de código que se ha de escribir en determinadas circunstancias.  
  
> [!WARNING]
>  No se permite el uso de `with` en modo strict.  El uso de `with` puede hacer que el código sea más difícil de leer y de depurar y debe evitarse por regla general.  
  
## Ejemplo  
 En este ejemplo, se utiliza el objeto `Math` varias veces:  
  
```javascript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## Ejemplo  
 Si vuelve a escribir el ejemplo para usar la instrucción `with`, el código se vuelve más conciso:  
  
```javascript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vea también  
 [this \(Instrucción\)](../../javascript/reference/this-statement-javascript.md)