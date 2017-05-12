---
title: "Int32Array (Objeto) | Microsoft Docs"
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
ms.assetid: 48696299-e41e-4590-b1b5-26fe19f68139
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Int32Array (Objeto)
Matriz con tipo de valores enteros de 32 bits.  El contenido se inicializa en 0.  Si el número de bytes solicitado no se puede asignar, se produce una excepción.  
  
## Sintaxis  
  
```  
  
      int32Array = new Int32Array( length );  
int32Array = new Int32Array( array );  
int32Array = new Int32Array( buffer, byteOffset, length);  
```  
  
## Parámetros  
 `int32Array`  
 Obligatorio.  Nombre de variable a la que se asigna el objeto **Int32Array**.  
  
 `length`  
 Especifica el número de elementos de la matriz.  
  
 `array`  
 Matriz \(o matriz con tipo\) incluida en esta matriz.  El contenido se inicializa en el contenido de la matriz o matriz con tipo especificada; todos los elementos se convierten al tipo Int32.  
  
 `buffer`  
 ArrayBuffer que el objeto Int32Array representa.  
  
 `byteOffset`  
 Opcional.  Especifica el desplazamiento en bytes desde el principio del búfer donde debe empezar el objeto Int32Array.  
  
 `length`  
 Número de elementos de la matriz.  
  
## Constantes  
 En la tabla siguiente se muestran las constantes del objeto `Int32Array`.  
  
|Constante|Descripción|  
|---------------|-----------------|  
|[BYTES\_PER\_ELEMENT \(Constante\)](../../javascript/reference/bytes-per-element-constant-int32array.md)|Tamaño en bytes de cada elemento de la matriz.|  
  
## Propiedades  
 En la tabla siguiente se muestran las constantes del objeto `Int32Array`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[buffer \(Propiedad\)](../../javascript/reference/buffer-property-int32array.md)|Solo lectura.  Obtiene el ArrayBuffer al que hace referencia esta matriz.|  
|[byteLength \(Propiedad\)](../../javascript/reference/bytelength-property-int32array.md)|Solo lectura.  Longitud de esta matriz desde el principio de su ArrayBuffer, en bytes, corregida en tiempo de construcción.|  
|[byteOffset \(Propiedad\)](../../javascript/reference/byteoffset-property-int32array.md)|Solo lectura.  Desplazamiento de esta matriz desde el principio de su ArrayBuffer, en bytes, corregido en tiempo de construcción.|  
|[length \(Propiedad\)](../../javascript/reference/length-property-int32array.md)|Longitud de la matriz.|  
  
## Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Int32Array`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[set \(Método, Int32Array\)](../../javascript/reference/set-method-int32array.md)|Establece un valor o una matriz de valores.|  
|[subarray \(Método, Int32Array\)](../../javascript/reference/subarray-method-int32array.md)|Obtiene una nueva vista de Int32Array del almacén de ArrayBuffer para esta matriz.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo usar un objeto Int32Array para procesar los datos binarios adquiridos de un objeto XmlHttpRequest:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]