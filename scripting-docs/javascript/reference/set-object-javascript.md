---
title: "Set (Objeto, JavaScript) | Microsoft Docs"
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
  - "Set"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4a4dd749-2a76-44fb-9cb0-a3ef317f75fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Set (Objeto, JavaScript)
Una colección de valores únicos que pueden ser de cualquier tipo.  
  
## Sintaxis  
  
```  
setObj = new Set()  
  
```  
  
## Comentarios  
 Si intenta agregar un valor que no sea único a `Set`, el nuevo valor no se agregará a la colección.  
  
## Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `Set`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[Constructor](../../javascript/reference/constructor-property-set.md)|Especifica la función que crea un conjunto.|  
|[prototipo](../../javascript/reference/prototype-property-set.md)|Devuelve una referencia al prototipo para un conjunto.|  
|[size](../../javascript/reference/size-property-set-javascript.md)|Devuelve el número de elementos de un conjunto.|  
  
## Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Set`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[agregar](../../javascript/reference/add-method-set-javascript.md)|Agrega un elemento a un conjunto.|  
|[clear](../../javascript/reference/clear-method-set-javascript.md)|Quita todos los elementos de un conjunto.|  
|[eliminar](../../javascript/reference/delete-method-set-javascript.md)|Quita un elemento especificado de un conjunto.|  
|[forEach](../../javascript/reference/foreach-method-set-javascript.md)|Realiza la acción especificada para cada elemento de un conjunto.|  
|[tiene](../../javascript/reference/has-method-set-javascript.md)|Devuelve el objeto `true` si el conjunto contiene un elemento especificado.|  
|[toString](../../javascript/reference/tostring-method-set-javascript.md)|Devuelve una representación de cadena de un conjunto.|  
|[valueOf](../../javascript/reference/valueof-method-set-javascript.md)|Devuelve el valor primitivo del objeto especificado.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo agregar miembros a un conjunto y después recuperarlos.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]