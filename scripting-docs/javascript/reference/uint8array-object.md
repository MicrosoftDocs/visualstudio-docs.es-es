---
title: "Uint8Array (Objeto) | Microsoft Docs"
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
ms.assetid: ae78b3ee-b660-4625-ac7b-d414a0842c87
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Uint8Array (Objeto)
Matriz con tipo de valores enteros sin signo de 8 bits.  El contenido se inicializa en 0.  Si el número de bytes solicitado no se puede asignar, se produce una excepción.  
  
## Sintaxis  
  
```  
  
      uint8Array = new Uint8Array( length );  
uint8Array = new Uint8Array( array );  
uint8Array = new Uint8Array( buffer, byteOffset, length);  
```  
  
## Parámetros  
 `uint8Array`  
 Obligatorio.  Nombre de variable a la que se asigna el objeto **Uint8Array**.  
  
 `length`  
 Especifica el número de elementos de la matriz.  
  
 `array`  
 Matriz \(o matriz con tipo\) incluida en esta matriz.  El contenido se inicializa en el contenido de la matriz o matriz con tipo especificada; todos los elementos se convierten al tipo Uint8.  
  
 `buffer`  
 ArrayBuffer que el objeto Uint8Array representa.  
  
 `byteOffset`  
 Opcional.  Especifica el desplazamiento en bytes desde el principio del búfer donde debe empezar el objeto Uint8Array.  
  
 `length`  
 Número de elementos de la matriz.  
  
## Constantes  
 En la tabla siguiente se muestran las constantes del objeto `Uint8Array`.  
  
|Constante|Descripción|  
|---------------|-----------------|  
|[BYTES\_PER\_ELEMENT \(Constante\)](../../javascript/reference/bytes-per-element-constant-uint8array.md)|Tamaño en bytes de cada elemento de la matriz.|  
  
## Propiedades  
 En la tabla siguiente se muestran las constantes del objeto `Uint8Array`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[buffer \(Propiedad\)](../../javascript/reference/buffer-property-uint8array.md)|Solo lectura.  Obtiene el ArrayBuffer al que hace referencia esta matriz.|  
|[byteLength \(Propiedad\)](../../javascript/reference/bytelength-property-uint8array.md)|Solo lectura.  Longitud de esta matriz desde el principio de su ArrayBuffer, en bytes, corregida en tiempo de construcción.|  
|[byteOffset \(Propiedad\)](../../javascript/reference/byteoffset-property-uint8array.md)|Solo lectura.  Desplazamiento de esta matriz desde el principio de su ArrayBuffer, en bytes, corregido en tiempo de construcción.|  
|[length \(Propiedad\)](../../javascript/reference/length-property-uint8array.md)|Longitud de la matriz.|  
|||  
  
## Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Uint8Array`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[set \(Método, Uint8Array\)](../../javascript/reference/set-method-uint8array.md)|Establece un valor o una matriz de valores.|  
|[subarray \(Método, Uint8Array\)](../../javascript/reference/subarray-method-uint8array.md)|Obtiene una nueva vista de Uint8Array del almacén de ArrayBuffer para esta matriz.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo usar un objeto Uint8Array para procesar los datos binarios adquiridos de un objeto XmlHttpRequest:  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint8Array(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]