---
title: "Objeto Uint8ClampedArray (JavaScript) | Microsoft Docs"
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
ms.assetid: 0c5537f7-00b4-487a-8fba-ef032e67e7bd
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Objeto Uint8ClampedArray (JavaScript)
Matriz con tipo de números enteros sin signo de 8 bits, con valores fijados entre 0 y 255.  El contenido se inicializa en 0.  Si el número de bytes solicitado no se puede asignar, se produce una excepción.  
  
## Sintaxis  
  
```  
  
uint8ClampedArray = new Uint8ClampedArray( length ); uint8ClampedArray = new Uint8ClampedArray( array ); uint8ClampedArray = new Uint8ClampedArray( buffer, byteOffset, length);  
```  
  
## Parámetros  
 `uint8ClampedArray`  
 Requerido.  Nombre de variable a la que se asigna el objeto `Uint8ClampedArray`.  
  
 `length`  
 Opcional.  Número de elementos de la matriz.  
  
 `array`  
 Opcional.  Matriz \(o matriz con tipo\) incluida en esta matriz.  El contenido se inicializa en el contenido de la matriz o matriz con tipo especificada; todos los elementos se convierten al tipo `Uint8`.  
  
 `buffer`  
 Opcional.  [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) que el objeto `Uint8ClampedArray` representa.  
  
 `byteOffset`  
 Opcional.  Desplazamiento en bytes desde el principio del búfer donde debe empezar el objeto `Uint8ClampedArray`.  
  
 `length`  
 Opcional.  Número de elementos de la matriz.  
  
## Comentarios  
 Los valores en un objeto `Uint8ClampedArray` se encuentran entre 0 y 255.  Si establece un valor negativo en un miembro de matriz, se define 0 como valor.  Si establece un valor superior a 255 en un miembro de matriz, se define 255 como valor.  
  
 Los valores en un objeto `Uint8ClampedArray` se redondean hacia el valor de evento más próximo, lo cual se denomina "redondeo bancario".  
  
## Constantes  
 En la tabla siguiente se muestran las constantes del objeto `Uint8ClampedArray`.  
  
|Constante|Descripción|  
|---------------|-----------------|  
|[BYTES\_PER\_ELEMENT \(Constante\)](../../javascript/reference/bytes-per-element-constant-uint8clampedarray.md)|Tamaño en bytes de cada elemento de la matriz.|  
  
## Propiedades  
 En la tabla siguiente se muestran las constantes del objeto `Uint8ClampedArray`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[buffer \(Propiedad\)](../../javascript/reference/buffer-property-uint8clampedarray.md)|Sólo lectura.  Obtiene el [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) al que hace referencia esta matriz.|  
|[byteLength \(Propiedad\)](../../javascript/reference/bytelength-property-uint8clampedarray.md)|Sólo lectura.  Longitud de esta matriz desde el principio de su [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), en bytes, corregida en tiempo de construcción.|  
|[byteOffset \(Propiedad\)](../../javascript/reference/byteoffset-property-uint8clampedarray.md)|Sólo lectura.  Desplazamiento de esta matriz desde el principio de su [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), en bytes, corregido en tiempo de construcción.|  
|[length \(Propiedad\)](../../javascript/reference/length-property-uint8clampedarray.md)|Longitud de la matriz.|  
  
## Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Uint8ClampedArray`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[set \(Método\)](../../javascript/reference/set-method-uint8clampedarray.md)|Establece un valor o una matriz de valores.|  
|[subarray \(Método\)](../../javascript/reference/subarray-method-uint8clampedarray.md)|Obtiene una nueva vista `Uint8ClampedArray` del almacén de [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) para esta matriz, especificando los primeros y últimos miembros de la submatriz.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo usar un objeto `Uint8ClampedArray` para procesar los datos binarios adquiridos de un objeto `XmlHttpRequest`:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint8ClampedArray(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Ejemplo  
 En el ejemplo siguiente, se muestra cómo los valores quedan restringidos en un objeto `Uint8ClampedArray`.  
  
```javascript  
var ints = new Uint8ClampedArray(2);  
ints[0] = -1;  // 0 will be assigned.  
ints[1] = 256; // 255 will be assigned.  
  
```  
  
## Ejemplo  
 En el ejemplo siguiente, se muestra cómo los valores se redondean en un objeto `Uint8ClampedArray`.  
  
```  
var ints = new Uint8ClampedArray(4);  
ints[0] = 11.3; // 11 will be assigned (same as Int8Array).  
ints[1] = 11.8; // 11 will be assigned (same as Int8Array).  
ints[2] = 10.5; // 10 will be assigned (rounded to the nearest   
                // even value).  
ints[3] = 11.5; // 12 will be assigned (rounded to the nearest   
                // even value).  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Vea también  
 [Uint8Array \(Objeto\)](../../javascript/reference/uint8array-object.md)   
 [ArrayBuffer \(Objeto\)](../../javascript/reference/arraybuffer-object.md)