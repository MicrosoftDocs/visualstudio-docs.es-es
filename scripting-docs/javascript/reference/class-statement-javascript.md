---
title: "Instrucción Class (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: bf45ebad-4678-4062-88df-55d32b603c69
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e828ae86c3f8f585179e3b097d98b3449c3f3b45
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="class-statement-javascript"></a>Instrucción class (JavaScript)
Declara una clase nueva.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class classname () [extends object] {    [constructor([arg1 [,... [,argN]]]) {        statements    }]    [[static] method([arg1 [,... [,argN]]]) {        statements    }]}  
```  
  
#### <a name="parameters"></a>Parámetros  
 `classname`  
 Obligatorio. Nombre de la clase.  
  
 `object`  
 Opcional. Objeto o clase de los que la nueva clase hereda propiedades y métodos.  
  
 `constructor`  
 Opcional. Función de constructor que inicializa la nueva instancia de clase.  
  
 `arg1...argN`  
 Opcional. Lista opcional separada por comas de los argumentos que la función entiende.  
  
 `statements`  
 Opcional. Una o varias instrucciones [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
 `static`  
 Opcional. Especifica un método estático.  
  
 `method`  
 Opcional. Una o varias instancias o métodos estáticos de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] a los que se puede llamar en una instancia de clase.  
  
## <a name="remarks"></a>Comentarios  
 Una clase permite crear objetos nuevos con herencia basada en el prototipo, constructores, métodos de instancia y métodos estáticos. Puede usar el objeto `super` dentro de un constructor de clase o un método de clase para llamar al mismo constructor o método del objeto o clase primaria. De manera opcional, use la instrucción `extends` después del nombre de clase para especificar la clase o el objeto de los que hereda métodos la nueva clase.  
  
## <a name="example"></a>Ejemplo  
  
```JavaScript  
class Spelunking extends EXPERIENCE.Outdoor {  
  constructor(name, location) {  
    super(name, location);  
  
    this.minSkill = Spelunking.defaultSkill();  
    //...  
  }  
  update(minSkill) {  
    //...  
    super.update(minSkill);  
  }  
  static defaultSkill() {  
    return new EXPERIENCE.Level3();  
  }  
}  
```  
  
## <a name="example"></a>Ejemplo  
 También puede crear nombres de propiedad calculada para las clases. En el ejemplo de código siguiente se crea un nombre de propiedad calculada mediante la sintaxis `set`.  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    set [propName](v) {  
        this.value = v;  
    }  
};  
  
var s = new Spelunking();  
console.log(s.value);  
s.prop_42 = 42;  
console.log(s.value);  
  
// Output:  
// undefined  
// 42  
  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se crea un nombre de propiedad para una clase dinámicamente mediante la sintaxis `get`.  
  
```JavaScript  
var propName = "prop_42";  
  
class Spelunking {  
    get [propName]() {  
        return 777;  
    }  
}  
  
var s = new Spelunking();  
console.log(s.prop_42);  
  
// Output:  
// 777  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12exp](../../javascript/reference/includes/jsv12exp-md.md)]