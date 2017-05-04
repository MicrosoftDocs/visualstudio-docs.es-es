---
title: "parseInt (Funci&#243;n de JavaScript) | Microsoft Docs"
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
  - "parseInt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "parseInt (método)"
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# parseInt (Funci&#243;n de JavaScript)
Convierte una cadena en un entero.  
  
## Sintaxis  
  
```  
parseInt(numString, [radix])   
```  
  
## Parámetros  
 `numString`  
 Obligatorio.  Cadena que se va a convertir en un número.  
  
 `radix`  
 Opcional.  Valor entre 2 y 36 que especifica la base del número en `numString`.  Si no se proporciona este argumento, las cadenas con un prefijo '0x' se consideran hexadecimales.  Todas las demás cadenas se consideran decimales.  
  
## Comentarios  
 La función `parseInt` devuelve un valor entero igual que el número contenido en `numString`.  Si no se puede analizar correctamente ningún prefijo de `numString` en un entero, se devuelve `NaN` \(no es un número\).  
  
```javascript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 Puedes comprobar si es `NaN` mediante la función `isNaN`.  
  
## Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Objeto Global](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  A partir de [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], la función `parseInt` no trata como un octal una cadena que tenga un prefijo '0'.  Sin embargo, cuando no se usa la función `parseInt`, las cadenas con un prefijo '0' se pueden seguir interpretando como octales.  Consulta [Tipos de datos](../../javascript/data-types-javascript.md) para obtener información sobre los enteros octales.  
  
## Vea también  
 [isNaN \(Función\)](../../javascript/reference/isnan-function-javascript.md)   
 [parseFloat \(Función\)](../../javascript/reference/parsefloat-function-javascript.md)   
 [String \(Objeto\)](../../javascript/reference/string-object-javascript.md)   
 [valueOf \(Método, Object\)](../../javascript/reference/valueof-method-object-javascript.md)