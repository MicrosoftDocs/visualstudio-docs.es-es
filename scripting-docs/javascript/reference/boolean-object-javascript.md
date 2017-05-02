---
title: "Boolean (Objeto de JavaScript) | Microsoft Docs"
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
  - "boolean_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Boolean (tipo de datos), Boolean (objeto)"
  - "Boolean (objeto)"
ms.assetid: d67748f2-7bf5-4889-8269-e777616cc5f0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Boolean (Objeto de JavaScript)
Crea un nuevo valor Boolean.  
  
## Sintaxis  
  
```  
  
boolObj = new Boolean([boolValue])  
```  
  
## Parámetros  
 `boolObj`  
 Obligatorio.  Nombre de variable al que se asigna el objeto `Boolean`.  
  
 `boolValue`  
 Opcional.  Valor Boolean inicial para el nuevo objeto.  Si se omite `boolvalue` o es `false`, 0, `null`, `NaN` o una cadena vacía, el valor inicial del objeto Boolean es `false`.  De lo contrario, el valor inicial es `true`.  
  
## Comentarios  
 El objeto `Boolean` es un contenedor para el tipo de datos Boolean.  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa implícitamente el objeto `Boolean` siempre que un tipo de datos Boolean se convierte en un objeto `Boolean`.  
  
 Normalmente no se crean instancias del objeto `Boolean` explícitamente.  
  
## Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `Boolean`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[constructor \(Propiedad\)](../../javascript/reference/constructor-property-boolean.md)|Especifica la función que crea un objeto Boolean.|  
|[prototype \(Propiedad\)](../../javascript/reference/prototype-property-boolean.md)|Devuelve una referencia al prototipo para un Boolean.|  
  
<a name="js56jsobjarraymeth"></a>   
## Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Boolean`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[toString \(Método\)](../../javascript/reference/tostring-method-boolean-1.md)|Devuelve una representación de cadena de un Boolean.|  
|[valueOf \(Método\)](../../javascript/reference/valueof-method-boolean.md)|Obtiene una referencia al Boolean.|  
  
## Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]