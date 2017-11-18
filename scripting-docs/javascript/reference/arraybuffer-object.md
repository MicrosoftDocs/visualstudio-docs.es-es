---
title: Objeto ArrayBuffer | Documentos de Microsoft
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
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c253d63d12a4a5e71d1661aae560b74debecdd62
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="arraybuffer-object"></a>ArrayBuffer (Objeto)
Representa un búfer de datos binarios sin formato que se usa para almacenar datos para las diferentes matrices con tipo. `ArrayBuffers`no se puede leer o escribir directamente, pero se pueden pasar a una matriz con tipo o [objeto DataView](../../javascript/reference/dataview-object.md) para interpretar el búfer sin formato según sea necesario.  
  
 Para obtener más información acerca de las matrices con tipo, consulte [las matrices con tipo](../../javascript/advanced/typed-arrays-javascript.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```JavaScript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## <a name="parameters"></a>Parámetros  
 `arrayBuffer`  
 Obligatorio. Nombre de variable a la que se asigna el objeto `ArrayBuffer`.  
  
 `length`  
 Longitud del búfer. El contenido del objeto ArrayBuffer se inicializa en 0. Si el número de bytes solicitado no se puede asignar, se produce una excepción.  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `ArrayBuffer`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[Propiedad byteLength](../../javascript/reference/bytelength-property-arraybuffer.md)|Sólo lectura. Longitud del objeto ArrayBuffer en bytes.|  
  
## <a name="functions"></a>Funciones  
 En la tabla siguiente se muestran las funciones del objeto `ArrayBuffer`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[ArrayBuffer.isView (función)](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|Determina si un objeto permite ver el búfer.|  
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos del objeto `ArrayBuffer`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[slice (método)](../../javascript/reference/slice-method-arraybuffer.md)|Devuelve una sección de `ArrayBuffer`.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar un objeto ArrayBuffer para procesar los datos binarios adquiridos de un [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx). Puede usar un [objeto DataView](../../javascript/reference/dataview-object.md) para obtener los valores individuales.  
  
```JavaScript  
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
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información sobre el uso de `XmlHttpRequest`, consulte [mejoras de XMLHttpRequest](http://msdn.microsoft.com/en-us/be09137c-6546-441b-b953-dcbf72b77069).  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]