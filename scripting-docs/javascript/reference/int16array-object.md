---
title: Objeto Int16Array | Documentos de Microsoft
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
ms.assetid: b87f36b4-4e38-4f32-b258-654c4ad2c615
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 550208f0f13ac05f96c13b240952d59ee62c097e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637825"
---
# <a name="int16array-object"></a>Int16Array (Objeto)
Una matriz con tipo de valores enteros de 16 bits. El contenido se inicializa en 0. Si el número de bytes solicitado no se puede asignar, se produce una excepción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      int16Array = new Int16Array( length );  
int16Array = new Int16Array( array );  
int16Array = new Int16Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parámetros  
 `int16Array`  
 Obligatorio. El nombre de variable a la que el **Int16Array** se asigna al objeto.  
  
 `length`  
 Especifica el número de elementos de la matriz.  
  
 `array`  
 Matriz (o matriz con tipo) incluida en esta matriz. El contenido se inicializa en el contenido de la matriz o matriz con tipo especificada; todos los elementos se convierten al tipo Int16.  
  
 `buffer`  
 ArrayBuffer que el objeto Int16Array representa.  
  
 `byteOffset`  
 Opcional. Especifica el desplazamiento en bytes desde el principio del búfer donde debe empezar el objeto Int16Array.  
  
 `length`  
 Número de elementos de la matriz.  
  
## <a name="constants"></a>Constantes  
 En la tabla siguiente se muestran las constantes del objeto `Int16Array`.  
  
|Constante|Descripción|  
|--------------|-----------------|  
|[BYTES_PER_ELEMENT (constante)](../../javascript/reference/bytes-per-element-constant-int16array.md)|Tamaño en bytes de cada elemento de la matriz.|  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las constantes del objeto `Int16Array`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[búfer de propiedad](../../javascript/reference/buffer-property-int16array.md)|Sólo lectura. Obtiene el ArrayBuffer al que hace referencia esta matriz.|  
|[Propiedad byteLength](../../javascript/reference/byteoffset-property-int16array.md)|Sólo lectura. Longitud de esta matriz desde el principio de su ArrayBuffer, en bytes, corregida en tiempo de construcción.|  
|[Propiedad byteOffset](../../javascript/reference/byteoffset-property-int16array.md)|Sólo lectura. Desplazamiento de esta matriz desde el principio de su ArrayBuffer, en bytes, corregido en tiempo de construcción.|  
|[Propiedad Length](../../javascript/reference/length-property-int16array.md)|Longitud de la matriz.|  
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos del objeto `Int16Array`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[set (Método, Int16Array)](../../javascript/reference/set-method-int16array.md)|Establece un valor o una matriz de valores.|  
|[subarray (Método, Int16Array)](../../javascript/reference/subarray-method-int16array.md)|Obtiene una nueva vista de Int16Array del almacén de ArrayBuffer para esta matriz.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar un objeto Int16Array para procesar los datos binarios adquiridos de un objeto XmlHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int16Array(buffer.byteLength / 2);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt16(i * 2);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]