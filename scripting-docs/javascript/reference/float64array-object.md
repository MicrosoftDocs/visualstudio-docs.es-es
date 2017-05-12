---
title: "Float64Array (Objeto) | Microsoft Docs"
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
ms.assetid: 74c945dc-56ae-458c-b0aa-782f240e9b6c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Float64Array (Objeto)
Matriz con tipo de valores float de 64 bits.  El contenido se inicializa en 0.  Si el número de bytes solicitado no se puede asignar, se produce una excepción.  
  
## Sintaxis  
  
```  
  
float64Array = new Float64Array( length ); float64Array = new Float64Array( array ); float64Array = new Float64Array( buffer, byteOffset, length);  
```  
  
## Parámetros  
 `float64Array`  
 Requerido.  Nombre de variable a la que se asigna el objeto **Float64Array**.  
  
 `length`  
 Especifica el número de elementos de la matriz.  
  
 `array`  
 Matriz \(o matriz con tipo\) incluida en esta matriz.  El contenido se inicializa en el contenido de la matriz o matriz con tipo especificada; todos los elementos se convierten al tipo Float64.  
  
 `buffer`  
 ArrayBuffer que el objeto Float64Array representa.  
  
 `byteOffset`  
 Opcional.  Especifica el desplazamiento en bytes desde el principio del búfer donde debe empezar el objeto Float64Array.  
  
 `length`  
 Número de elementos de la matriz.  
  
## Constantes  
 En la tabla siguiente se muestran las constantes del objeto `Float64Array`.  
  
|Constante|Descripción|  
|---------------|-----------------|  
|[BYTES\_PER\_ELEMENT \(Constante\)](../../javascript/reference/bytes-per-element-constant-float64array.md)|Tamaño en bytes de cada elemento de la matriz.|  
  
## Propiedades  
 En la tabla siguiente se muestran las constantes del objeto `Float64Array`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[buffer \(Propiedad\)](../../javascript/reference/bytelength-property-float64array.md)|Sólo lectura.  Obtiene el ArrayBuffer al que hace referencia esta matriz.|  
|[byteLength \(Propiedad\)](../../javascript/reference/bytelength-property-float64array.md)|Sólo lectura.  Longitud de esta matriz desde el principio de su ArrayBuffer, en bytes, corregida en tiempo de construcción.|  
|[byteOffset \(Propiedad\)](../../javascript/reference/length-property-float64array.md)|Sólo lectura.  Desplazamiento de esta matriz desde el principio de su ArrayBuffer, en bytes, corregido en tiempo de construcción.|  
|[length \(Propiedad\)](../../javascript/reference/length-property-float64array.md)|Longitud de la matriz.|  
  
## Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Float64Array`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[get \(Método\)](../../javascript/reference/get-method-float64array.md)|Se puede omitir.  Obtiene el elemento en el índice especificado.|  
|[set \(Método, Float64Array\)](../../javascript/reference/set-method-float64array.md)|Establece un valor o una matriz de valores.|  
|[subarray \(Método, Float64Array\)](../../javascript/reference/subarray-method-float64array.md)|Obtiene una nueva vista de Float64Array del almacén de ArrayBuffer para esta matriz.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo usar un objeto Float64Array para procesar los datos binarios adquiridos de un objeto XmlHttpRequest:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Float64Array(buffer.byteLength / 8);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getFloat64(i * 8);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]