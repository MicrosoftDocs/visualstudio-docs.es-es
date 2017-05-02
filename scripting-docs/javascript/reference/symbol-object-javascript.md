---
title: "Objeto Symbol (JavaScript) | Microsoft Docs"
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
ms.assetid: 2ad059f1-4b7f-4758-882a-c74ce1283ab0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Objeto Symbol (JavaScript)
Le permite crear un identificador único.  
  
## Sintaxis  
  
```  
obj = Symbol(desc)  
```  
  
#### Parámetros  
 `desc`  
 Opcional.  La descripción del símbolo.  
  
## Comentarios  
 Los objetos Símbolo permiten agregar propiedades a los objetos existentes sin posibilidad de interferencias con las propiedades de objeto existentes, sin visibilidad no intencionada y sin otras adiciones no coordinadas por parte de otro código.  
  
 Símbolo es un tipo de datos primitivo.  Los objetos Símbolo no se pueden crear mediante el operador `new`.  
  
 Para agregar objetos de símbolo al registro de símbolos globales, use las funciones `Symbol.for` y `Symbol.keyFor`.  Si serializa símbolos como cadenas, utilice el registro de símbolos globales para asegurarse de que se asigne una cadena concreta al símbolo correcto para todas las búsquedas.  
  
 JavaScript incluye los siguientes valores de símbolo integrados que están disponibles en el ámbito global.  
  
|Símbolo|Descripción|  
|-------------|-----------------|  
|`Symbol.hasInstance`|Este método determina si un objeto de constructor reconoce un objeto como una de las instancias del constructor.  El operador `instanceof` lo utiliza internamente.|  
|`Symbol.isConcatSpreadable`|Esta propiedad devuelve un valor booleano que indica si `Array.concat` debe aplanar un objeto a sus elementos de matriz.|  
|`Symbol.iterator`|Este método devuelve el iterador predeterminado de un objeto.  La instrucción `for…of` lo utiliza internamente.|  
|`Symbol.toPrimitive`|Este método convierte un objeto en un valor primitivo correspondiente.  La operación abstracta `ToPrimitive` lo utiliza internamente.|  
|`Symbol.toStringTag`|Esta propiedad devuelve un valor de cadena que se utiliza para ayudar a crear la descripción de cadena predeterminada de un objeto.  El método integrado `Object.toString` lo utiliza internamente.|  
|`Symbol.unscopables`|Esta propiedad devuelve un objeto cuyas propiedades se excluyen de los enlaces del entorno `with` del objeto asociado.|  
  
## Funciones  
 En la tabla siguiente se muestran las funciones del objeto `Symbol`.  
  
|||  
|-|-|  
|Propiedad|Descripción|  
|[Symbol.for](../../javascript/reference/symbol-for-function-javascript.md)|Devuelve el símbolo de una clave especificada o , si la clave no está presente, crea un nuevo objeto de símbolo con la nueva clave.|  
|[Symbol.keyFor](../../javascript/reference/symbol-keyfor-function-javascript.md)|Devuelve la clave de un símbolo especificado.|  
|||  
  
## Ejemplo  
  
```javascript  
(function() {  
  
    // module-scoped symbol  
    var key = Symbol("description");  
  
    function MyClass(privateData) {  
      this[key] = privateData;  
    }  
  
    MyClass.prototype = {  
      someFunc: function() {  
        return "data: " + this[key];  
      }  
    };  
  
    var c = new MyClass("private data")  
    console.log(key);  
    console.log(c["key"]);  
    console.log(c.someFunc());  
  
})();  
  
// Output:  
// undefined  
// undefined  
// data: private data  
```  
  
## Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]