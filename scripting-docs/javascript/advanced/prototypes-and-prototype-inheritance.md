---
title: Prototipos y herencia de prototipos | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- prototype [JavaScript]
- prototype inheritance [JavaScript]
ms.assetid: 1e1d0631-2a9f-4011-b9fe-fa338e1ef34c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 3fb5627d2cc92c36e9dcf34f4b94796b6620321f
ms.openlocfilehash: ade60bcbbfad166bae18b650daa6906f9983d4cd
ms.contentlocale: es-es
ms.lasthandoff: 08/11/2017

---
# <a name="prototypes-and-prototype-inheritance"></a>Prototipos y herencia de prototipos
En JavaScript, `prototype` es una propiedad de funciones, y de objetos creados por las funciones constructoras. El prototipo de una función es un objeto. Se usa principalmente cuando se utiliza una función como constructor.  
  
```JavaScript  
function Vehicle(wheels, engine) {  
    this.wheels = wheels;  
    this.engine = engine;  
}  
```  
  
 En el ejemplo anterior, el prototipo de la función `Vehicle` es el prototipo de cualquier objeto cuyas instancias se crean con el constructor `Vehicle`.  
  
## <a name="using-prototypes-to-add-properties-and-methods"></a>Usar prototipos para agregar propiedades y métodos  
 Puedes usar la propiedad `prototype` para agregar propiedades y métodos a los objetos, incluso a los que ya se han creado:  
  
```JavaScript  
var testVehicle = new Vehicle(2, false);  
Vehicle.prototype.color = "red";  
var testColor = testVehicle.color;  
```  
  
 El valor de `testColor` es "red".  
  
 Puede incluso agregar propiedades y métodos a objetos predefinidos. Por ejemplo, puede definir un método `Trim` para el objeto prototipo `String`. Todas las cadenas del script heredarán el método.  
  
```JavaScript  
String.prototype.trim = function()  
{  
    // Replace leading and trailing spaces with the empty string  
    return this.replace(/(^\s*)|(\s*$)/g, "");  
}  
var s = "    leading and trailing spaces    ";  
// Displays "    leading and trailing spaces     (35)"  
window.alert(s + " (" + s.length + ")");  
// Remove the leading and trailing spaces  
s = s.trim();  
// Displays "leading and trailing spaces (27)"  
window.alert(s + " (" + s.length + ")");  
```  
  
### <a name="using-prototypes-to-derive-one-object-from-another-with-objectcreate"></a>Usar prototipos para derivar un objeto de otro con Object.create  

El prototipo `Object` se puede usar para derivar un objeto de otro. Por ejemplo, puede usar la función [Object.create](../../javascript/reference/object-create-function-javascript.md) para derivar un nuevo objeto `Bicycle` con el prototipo del objeto `Vehicle` que hemos definido antes (además de todas las propiedades nuevas que necesite).  
  
```JavaScript  
var bicycle = Object.create(Object.getPrototypeOf(Vehicle), {  
    "pedals" :{value: true}  
});  
  
```  
  
 El objeto `bicycle` tiene las propiedades `wheels`, `engine`, `color` y `pedals`, y su prototipo es `Vehicle.prototype`. El motor de JavaScript encuentra la propiedad `pedals` en `bicycle` y busca la cadena de prototipo para encontrar las propiedades `wheels`, `engine` y `color` de `Vehicle`.  
  
### <a name="changing-an-objects-prototype"></a>Cambiar el prototipo de un objeto  
 En Internet Explorer 11, puede reemplazar el prototipo interno de un objeto o función por un nuevo prototipo mediante la propiedad [__proto\_\_](../../javascript/reference/proto-property-object-javascript.md). Al utilizar esta propiedad, se heredan las propiedades y métodos del nuevo prototipo junto con otras propiedades y métodos en la cadena de prototipos.  
  
 En el ejemplo siguiente se muestra cómo modificar el prototipo de un objeto. Este ejemplo muestra cómo las propiedades heredadas del objeto cambian cuando cambia el prototipo.  
  
```JavaScript  
function Friend() {  
    this.demeanor = "happy";  
}  
  
function Foe() {  
    this.demeanor = "suspicious";  
}  
  
var friend = new Friend();  
var foe = new Foe();  
  
var player = new Object();  
player.__proto__ = foe;  
  
friend.ally = "Tom";  
  
if (console && console.log) {  
    console.log(player.demeanor === "happy" );      // Returns false  
    console.log(player.demeanor === "suspicious");  // Returns true  
    console.log(player.ally === "Tom");             // Returns false  
    // Turn the foe to a friend.  
    player.__proto__ = friend;  
    console.log(player.demeanor === "happy");       // Returns true  
    console.log(player.demeanor === "suspicious");  // Returns false  
    console.log(player.ally === "Tom");             // Returns true  
}  
```

