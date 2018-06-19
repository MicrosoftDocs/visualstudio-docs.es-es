---
title: Objeto Uint16Array | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: e684647d-04d0-41a9-9089-16612e18ec7d
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 447c0509a29f1696e0204d6f37ff88d3c0bdecae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641705"
---
# <a name="uint16array-object"></a>Uint16Array (Objeto)
Una matriz con tipo de valores enteros sin signo de 16 bits. El contenido se inicializa en 0. Si el número de bytes solicitado no se puede asignar, se produce una excepción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      uint16Array = new Uint16Array( length );  
uint16Array = new Uint16Array( array );  
uint16Array = new Uint16Array( buffer, byteOffset, length );  
```  
  
## <a name="parameters"></a>Parámetros  
 `uint16Array`  
 Obligatorio. El nombre de variable a la que el **Uint16Array** se asigna al objeto.  
  
 `length`  
 Especifica el número de elementos de la matriz.  
  
 `array`  
 Matriz (o matriz con tipo) incluida en esta matriz. El contenido se inicializa en el contenido de la matriz o matriz con tipo especificada; todos los elementos se convierten al tipo Uint16.  
  
 `buffer`  
 ArrayBuffer que el objeto Uint16Array representa.  
  
 `byteOffset`  
 Opcional. Especifica el desplazamiento en bytes desde el principio del búfer donde debe empezar el objeto Uint16Array.  
  
 `length`  
 Número de elementos de la matriz.  
  
## <a name="constants"></a>Constantes  
 En la tabla siguiente se muestran las constantes del objeto `Uint16Array`.  
  
|Constante|Descripción|  
|--------------|-----------------|  
|[BYTES_PER_ELEMENT (constante)](../../javascript/reference/bytes-per-element-constant-uint16array.md)|Tamaño en bytes de cada elemento de la matriz.|  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las constantes del objeto `Uint16Array`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[búfer de propiedad](../../javascript/reference/buffer-property-uint16array.md)|Sólo lectura. Obtiene el ArrayBuffer al que hace referencia esta matriz.|  
|[Propiedad byteLength](../../javascript/reference/bytelength-property-uint16array.md)|Sólo lectura. Longitud de esta matriz desde el principio de su ArrayBuffer, en bytes, corregida en tiempo de construcción.|  
|[Propiedad byteOffset](../../javascript/reference/byteoffset-property-uint16array.md)|Sólo lectura. Desplazamiento de esta matriz desde el principio de su ArrayBuffer, en bytes, corregido en tiempo de construcción.|  
|[Propiedad Length](../../javascript/reference/length-property-uint16array.md)|Longitud de la matriz.|  
|||  
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Uint16Array`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[set (Método, Uint16Array)](../../javascript/reference/set-method-uint16array.md)|Establece un valor o una matriz de valores.|  
|[subarray (Método, Uint16Array)](../../javascript/reference/subarray-method-uint16array.md)|Obtiene una nueva vista de Uint16Array del almacén de ArrayBuffer para esta matriz.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar un objeto Uint16Array para procesar los datos binarios adquiridos de un objeto XmlHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint16Array(buffer.byteLength / 2);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint16(i * 2);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]