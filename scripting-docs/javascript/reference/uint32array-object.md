---
title: "Uint32Array (Objeto) | Microsoft Docs"
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
ms.assetid: c4bf5409-2d4b-4660-9f4b-a45d7a02b47e
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Uint32Array (Objeto)
Matriz con tipo de valores enteros sin signo de 32 bits.  El contenido se inicializa en 0.  Si el número de bytes solicitado no se puede asignar, se produce una excepción.  
  
## Sintaxis  
  
```  
  
      uint32Array = new Uint32Array( length );  
uint32Array = new Uint32Array( array );  
uint32Array = new Uint32Array( buffer, byteOffset, length);  
```  
  
## Parámetros  
 `uint32Array`  
 Obligatorio.  Nombre de variable a la que se asigna el objeto **Uint32Array**.  
  
 `length`  
 Especifica el número de elementos de la matriz.  
  
 `array`  
 Matriz \(o matriz con tipo\) incluida en esta matriz.  El contenido se inicializa en el contenido de la matriz o matriz con tipo especificada; todos los elementos se convierten al tipo Uint32.  
  
 `buffer`  
 ArrayBuffer que el objeto Uint32Array representa.  
  
 `byteOffset`  
 Opcional.  Especifica el desplazamiento en bytes desde el principio del búfer donde debe empezar el objeto Uint32Array.  
  
 `length`  
 Número de elementos de la matriz.  
  
## Constantes  
 En la tabla siguiente se muestran las constantes del objeto `Uint32Array`.  
  
|Constante|Descripción|  
|---------------|-----------------|  
|[BYTES\_PER\_ELEMENT \(Constante\)](../../javascript/reference/bytes-per-element-constant-uint32array.md)|Tamaño en bytes de cada elemento de la matriz.|  
  
## Propiedades  
 En la tabla siguiente se muestran las constantes del objeto `Uint32Array`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[buffer \(Propiedad\)](../../javascript/reference/buffer-property-uint32array.md)|Solo lectura.  Obtiene el ArrayBuffer al que hace referencia esta matriz.|  
|[byteLength \(Propiedad\)](../../javascript/reference/bytelength-property-uint32array.md)|Solo lectura.  Longitud de esta matriz desde el principio de su ArrayBuffer, en bytes, corregida en tiempo de construcción.|  
|[byteOffset \(Propiedad\)](../../javascript/reference/byteoffset-property-uint32array.md)|Solo lectura.  Desplazamiento de esta matriz desde el principio de su ArrayBuffer, en bytes, corregido en tiempo de construcción.|  
|[length \(Propiedad\)](../../javascript/reference/length-property-uint32array.md)|Longitud de la matriz.|  
  
## Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Uint32Array`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[set \(Método, Uint32Array\)](../../javascript/reference/set-method-uint32array.md)|Establece un valor o una matriz de valores.|  
|[subarray \(Método, Uint32Array\)](../../javascript/reference/subarray-method-uint32array.md)|Obtiene una nueva vista de Uint32Array del almacén de ArrayBuffer para esta matriz.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo usar un objeto Uint32Array para procesar los datos binarios adquiridos de un objeto XMLHttpRequest:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]