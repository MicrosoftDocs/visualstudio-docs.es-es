---
title: "Object.getOwnPropertyDescriptor (Funci&#243;n de JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getOwnPropertyDescriptor (método) [JavaScript]"
ms.assetid: 8f0e1c90-c4f9-44c4-bf76-726bacecbc14
caps.latest.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 45
---
# Object.getOwnPropertyDescriptor (Funci&#243;n de JavaScript)
Obtiene el descriptor de propiedad propia del objeto especificado.  Un descriptor de propiedad propia es aquel que se define directamente en el objeto y no se hereda del prototipo del objeto.  
  
## Sintaxis  
  
```  
Object.getOwnPropertyDescriptor(object, propertyname)  
```  
  
## Parámetros  
 `object`  
 Obligatorio.  El objeto que contiene la propiedad.  
  
 `propertyname`  
 Obligatorio.  Nombre de la propiedad.  
  
## Valor devuelto  
 Descriptor de la propiedad.  
  
## Comentarios  
 Puede usar la función `Object.getOwnPropertyDescriptor` para obtener un objeto de descriptor que describa los atributos de la propiedad.  
  
 El [Object.defineProperty \(Función\)](../../javascript/reference/object-defineproperty-function-javascript.md) se usa para agregar o modificar las propiedades.  
  
## Ejemplo de propiedad de datos  
 En el ejemplo siguiente se obtiene un descriptor de propiedad de datos y se usa para hacer que la propiedad sea de solo lectura.  
  
```javascript  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property.  
obj.newDataProperty = "abc";  
  
// Get the property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// Change a property attribute.  
descriptor.writable = false;  
Object.defineProperty(obj, "newDataProperty", descriptor);  
  
```  
  
 Para obtener una lista de los atributos de propiedad, puede agregar el código siguiente a este ejemplo.  
  
```javascript  
// Get the descriptor from the object.  
var desc2 = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// List the descriptor attributes.  
for (var prop in desc2) {  
    document.write(prop + ': ' + desc2[prop]);  
    document.write("<br />");  
}  
  
// Output:  
// value: abc  
// writable: false  
// enumerable: true  
// configurable: true  
```  
  
## Requisitos  
 Se admiten todas las características en [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)].  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] admite objetos DOM, pero no objetos definidos por el usuario.  Se pueden especificar los atributos `enumerable` y `configurable`, aunque no se usan.  
  
## Vea también  
 [Prototipos de modelo de objetos de documento, parte 2: compatibilidad con descriptores de acceso \(captador\/establecedor\)](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Object.defineProperty \(Función\)](../../javascript/reference/object-defineproperty-function-javascript.md)