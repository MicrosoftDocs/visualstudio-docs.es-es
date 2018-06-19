---
title: Objeto DataView | Documentos de Microsoft
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
ms.assetid: 250ec067-7505-4ee0-82ab-bfd3c2820afa
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 370ee1afbdf7fe1d87843c4979833d54a575a4fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637275"
---
# <a name="dataview-object"></a>DataView (Objeto)
Puede usar un objeto DataView para leer y escribir los diferentes tipos de datos binarios en cualquier ubicación del objeto arraybuffer.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dataView = new DataView(buffer, byteOffset, byteLength);  
```  
  
## <a name="parameters"></a>Parámetros  
 `dataView`  
 Obligatorio. El nombre de variable a la que el **DataView** se asigna al objeto.  
  
 `buffer`  
 ArrayBuffer que representa la vista de datos.  
  
 `byteOffset`  
 Opcional. Especifica el desplazamiento en bytes desde el principio del búfer donde debe empezar la DataView.  
  
 `byteLength`  
 Opcional. Especifica la longitud (en bytes) de la sección del búfer que se debe representar la vista de datos.  
  
## <a name="remarks"></a>Comentarios  
 Si se omiten byteOffset y byteLength, DataView abarca todo el rango de ArrayBuffer. Si se omite el valor byteLength, DataView se extiende desde el byteOffset especificado hasta el final del objeto ArrayBuffer. Si el byteOffset determinado y byteLength hace referencia a un área más allá del final del objeto ArrayBuffer, se produce una excepción.  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `DataView`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[búfer de propiedad](../../javascript/reference/buffer-property-dataview.md)|Sólo lectura. Obtiene el ArrayBuffer al que se hace referencia a esta vista.|  
|[Propiedad byteLength](../../javascript/reference/bytelength-property-dataview.md)|Sólo lectura. Longitud de esta vista desde el principio de su ArrayBuffer, en bytes, corregida en tiempo de construcción.|  
|[Propiedad byteOffset](../../javascript/reference/byteoffset-property-dataview.md)|Sólo lectura. El desplazamiento de esta vista desde el principio de su ArrayBuffer, en bytes, corregida en tiempo de construcción.|  
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos del objeto `DataView`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[getInt8 (método)](../../javascript/reference/getint8-method-dataview.md)|Obtiene el valor Int8 en el desplazamiento de bytes especificado desde el principio de la vista.|  
|[getUint8 (Método, DataView)](../../javascript/reference/getuint8-method-dataview.md)|Obtiene el valor de Uint8 en el desplazamiento de bytes especificado desde el principio de la vista.|  
|[getInt16 (Método, DataView)](../../javascript/reference/getint16-method-dataview.md)|Obtiene el valor de tipo Int16 en el desplazamiento de bytes especificado desde el principio de la vista.|  
|[getUint16 (Método, DataView)](../../javascript/reference/getuint16-method-dataview.md)|Obtiene el valor de Uint16 en el desplazamiento de bytes especificado desde el principio de la vista.|  
|[getInt32 (Método, DataView)](../../javascript/reference/getint32-method-dataview.md)|Obtiene el valor Int32 en el desplazamiento de bytes especificado desde el principio de la vista.|  
|[getUint32 (Método, DataView)](../../javascript/reference/getuint32-method-dataview.md)|Obtiene el valor de Uint32 en el desplazamiento de bytes especificado desde el principio de la vista.|  
|[getFloat32 (Método, DataView)](../../javascript/reference/getfloat32-method-dataview.md)|Obtiene el valor Float32 en el desplazamiento de bytes especificado desde el principio de la vista.|  
|[getFloat64 (Método, DataView)](../../javascript/reference/getfloat64-method-dataview.md)|Obtiene el valor Float64 en el desplazamiento de bytes especificado desde el principio de la vista.|  
|[setInt8 (Método, DataView)](../../javascript/reference/setint8-method-dataview.md)|Almacena un valor Int8 en el desplazamiento de bytes especificado desde el principio de la vista.|  
|[setUint8 (Método, DataView)](../../javascript/reference/setuint8-method-dataview.md)|Almacena un valor de Uint8 en el desplazamiento de bytes especificado desde el principio de la vista.|  
|[setInt16 (Método, DataView)](../../javascript/reference/setint16-method-dataview.md)|Almacena un valor de tipo Int16 en el desplazamiento de bytes especificado desde el principio de la vista.|  
|[setUint16 (Método, DataView)](../../javascript/reference/setuint16-method-dataview.md)|Almacena un valor Uint16 en el desplazamiento de bytes especificado desde el principio de la vista.|  
|[setInt32 (Método, DataView)](../../javascript/reference/setint32-method-dataview.md)|Almacena un valor Int32 en el desplazamiento de bytes especificado desde el principio de la vista.|  
|[setUint32 (Método, DataView)](../../javascript/reference/setuint32-method-dataview.md)|Almacena un valor de Uint32 en el desplazamiento de bytes especificado desde el principio de la vista.|  
|[setFloat32 (Método, DataView)](../../javascript/reference/setfloat32-method-dataview.md)|Almacena un valor Float32 en el desplazamiento de bytes especificado desde el principio de la vista.|  
|[setFloat64 (Método, DataView)](../../javascript/reference/setfloat64-method-dataview.md)|Almacena un valor Float64 en el desplazamiento de bytes especificado desde el principio de la vista.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar un objeto DataView para procesar los datos binarios adquiridos de un objeto XmlHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var ints = new Int32Array(dataView.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]