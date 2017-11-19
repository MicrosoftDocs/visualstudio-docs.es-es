---
title: Objeto Uint32Array | Documentos de Microsoft
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
ms.assetid: c4bf5409-2d4b-4660-9f4b-a45d7a02b47e
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05f185e02ac117491d067ddca6605197d126620e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="uint32array-object"></a>Uint32Array (Objeto)
Una matriz con tipo de valores enteros sin signo de 32 bits. El contenido se inicializa en 0. Si el número de bytes solicitado no se puede asignar, se produce una excepción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      uint32Array = new Uint32Array( length );  
uint32Array = new Uint32Array( array );  
uint32Array = new Uint32Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parámetros  
 `uint32Array`  
 Obligatorio. El nombre de variable a la que el **Uint32Array** se asigna al objeto.  
  
 `length`  
 Especifica el número de elementos de la matriz.  
  
 `array`  
 Matriz (o matriz con tipo) incluida en esta matriz. El contenido se inicializa en el contenido de la matriz o matriz con tipo especificada; todos los elementos se convierten al tipo Uint32.  
  
 `buffer`  
 ArrayBuffer que el objeto Uint32Array representa.  
  
 `byteOffset`  
 Opcional. Especifica el desplazamiento en bytes desde el principio del búfer donde debe empezar el objeto Uint32Array.  
  
 `length`  
 Número de elementos de la matriz.  
  
## <a name="constants"></a>Constantes  
 En la tabla siguiente se muestran las constantes del objeto `Uint32Array`.  
  
|Constante|Descripción|  
|--------------|-----------------|  
|[BYTES_PER_ELEMENT (constante)](../../javascript/reference/bytes-per-element-constant-uint32array.md)|Tamaño en bytes de cada elemento de la matriz.|  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las constantes del objeto `Uint32Array`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[búfer de propiedad](../../javascript/reference/buffer-property-uint32array.md)|Sólo lectura. Obtiene el ArrayBuffer al que hace referencia esta matriz.|  
|[Propiedad byteLength](../../javascript/reference/bytelength-property-uint32array.md)|Sólo lectura. Longitud de esta matriz desde el principio de su ArrayBuffer, en bytes, corregida en tiempo de construcción.|  
|[Propiedad byteOffset](../../javascript/reference/byteoffset-property-uint32array.md)|Sólo lectura. Desplazamiento de esta matriz desde el principio de su ArrayBuffer, en bytes, corregido en tiempo de construcción.|  
|[Propiedad Length](../../javascript/reference/length-property-uint32array.md)|Longitud de la matriz.|  
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Uint32Array`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[set (Método, Uint32Array)](../../javascript/reference/set-method-uint32array.md)|Establece un valor o una matriz de valores.|  
|[subarray (Método, Uint32Array)](../../javascript/reference/subarray-method-uint32array.md)|Obtiene una nueva vista de Uint32Array del almacén de ArrayBuffer para esta matriz.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar un objeto Uint32Array para procesar los datos binarios adquiridos de un objeto XMLHttpRequest:  
  
```JavaScript  
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
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]