---
title: Objeto Uint8ClampedArray (JavaScript) | Documentos de Microsoft
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
ms.assetid: 0c5537f7-00b4-487a-8fba-ef032e67e7bd
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51673eadc8eb905355bf136dc82b2f240462180a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="uint8clampedarray-object-javascript"></a>Objeto Uint8ClampedArray (JavaScript)
Matriz con tipo de números enteros sin signo de 8 bits, con valores fijados entre 0 y 255. El contenido se inicializa en 0. Si el número de bytes solicitado no se puede asignar, se produce una excepción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      uint8ClampedArray = new Uint8ClampedArray( length );  
uint8ClampedArray = new Uint8ClampedArray( array );  
uint8ClampedArray = new Uint8ClampedArray( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parámetros  
 `uint8ClampedArray`  
 Obligatorio. Nombre de variable a la que se asigna el objeto `Uint8ClampedArray`.  
  
 `length`  
 Opcional. Número de elementos de la matriz.  
  
 `array`  
 Opcional. Matriz (o matriz con tipo) incluida en esta matriz. El contenido se inicializa en el contenido de la matriz o matriz con tipo especificada; todos los elementos se convierten al tipo `Uint8`.  
  
 `buffer`  
 Opcional. El [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) que la `Uint8ClampedArray` representa.  
  
 `byteOffset`  
 Opcional. Desplazamiento en bytes desde el principio del búfer donde debe empezar el objeto `Uint8ClampedArray`.  
  
 `length`  
 Opcional. Número de elementos de la matriz.  
  
## <a name="remarks"></a>Comentarios  
 Los valores en un objeto `Uint8ClampedArray` se encuentran entre 0 y 255. Si establece un valor negativo en un miembro de matriz, se define 0 como valor. Si establece un valor superior a 255 en un miembro de matriz, se define 255 como valor.  
  
 Los valores en un `Uint8ClampedArray` objeto se redondean a la más próximo al valor incluso, lo cual se denomina redondeo bancario.  
  
## <a name="constants"></a>Constantes  
 En la tabla siguiente se muestran las constantes del objeto `Uint8ClampedArray`.  
  
|Constante|Descripción|  
|--------------|-----------------|  
|[BYTES_PER_ELEMENT (constante)](../../javascript/reference/bytes-per-element-constant-uint8clampedarray.md)|Tamaño en bytes de cada elemento de la matriz.|  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las constantes del objeto `Uint8ClampedArray`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[búfer de propiedad](../../javascript/reference/buffer-property-uint8clampedarray.md)|Sólo lectura. Obtiene el [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) al que hace referencia esta matriz.|  
|[Propiedad byteLength](../../javascript/reference/bytelength-property-uint8clampedarray.md)|Sólo lectura. La longitud de esta matriz desde el principio de su [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), en bytes, corregida en tiempo de construcción.|  
|[Propiedad byteOffset](../../javascript/reference/byteoffset-property-uint8clampedarray.md)|Sólo lectura. El desplazamiento de esta matriz desde el principio de su [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), en bytes, corregida en tiempo de construcción.|  
|[Propiedad Length](../../javascript/reference/length-property-uint8clampedarray.md)|Longitud de la matriz.|  
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Uint8ClampedArray`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[establecer método](../../javascript/reference/set-method-uint8clampedarray.md)|Establece un valor o una matriz de valores.|  
|[subarray (método)](../../javascript/reference/subarray-method-uint8clampedarray.md)|Obtiene un nuevo `Uint8ClampedArray` ver de la [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) almacenar para esta matriz, especificando el primer y último elemento de la submatriz.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar un objeto `Uint8ClampedArray` para procesar los datos binarios adquiridos de un objeto `XmlHttpRequest`:  
  
```JavaScript  
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
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se muestra cómo los valores quedan restringidos en un objeto `Uint8ClampedArray`.  
  
```JavaScript  
var ints = new Uint8ClampedArray(2);  
ints[0] = -1;  // 0 will be assigned.  
ints[1] = 256; // 255 will be assigned.  
  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se muestra cómo los valores se redondean en un objeto `Uint8ClampedArray`.  
  
```  
var ints = new Uint8ClampedArray(4);  
ints[0] = 11.3; // 11 will be assigned (same as Int8Array).  
ints[1] = 11.8; // 12 will be assigned (same as Int8Array).  
ints[2] = 10.5; // 10 will be assigned (rounded to the nearest   
                // even value).  
ints[3] = 11.5; // 12 will be assigned (rounded to the nearest   
                // even value).  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Objeto Uint8Array](../../javascript/reference/uint8array-object.md)   
 [ArrayBuffer (Objeto)](../../javascript/reference/arraybuffer-object.md)
