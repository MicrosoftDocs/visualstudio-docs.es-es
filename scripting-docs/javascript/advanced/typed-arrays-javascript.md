---
title: Matrices con tipo (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: fa82c562-0ebf-4559-aecc-166e59f7fb64
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5fc3b29a4593e7c627a6e606242229e87fa5be54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="typed-arrays-javascript"></a>Matrices con tipo (JavaScript)
Puede usar matrices con tipo para controlar datos binarios de orígenes como protocolos de red, formatos de archivo binario y búferes de gráficos sin procesar. Las matrices con tipo también pueden usarse para administrar datos binarios en memoria con diseños de byte conocidos.  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente se muestra cómo usar un [objeto ArrayBuffer](../../javascript/reference/arraybuffer-object.md) como respuesta de [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx). Puede manipular los bytes de la respuesta usando los distintos métodos del [objeto DataView](../../javascript/reference/dataview-object.md) o copiando los bytes en la matriz con tipo correspondiente.  
  
> [!TIP]
>  Para más información sobre el uso de los diferentes tipos de respuestas con `XmlHttpRequest`, vea [XMLHttpRequest.responseType](http://msdn.microsoft.com/en-us/8d7738d1-4bfd-4cf1-8015-174def089556), [Mejoras de XMLHttpRequest](http://msdn.microsoft.com/en-us/be09137c-6546-441b-b953-dcbf72b77069) y [Descarga de distintos tipos de contenido (aplicaciones de la Tienda Windows)](http://msdn.microsoft.com/en-us/c0006bbd-17f9-4c6a-af81-2acaf109111d).  
  
```JavaScript  
...  
<div id="xhrDiv"></div>  
...  
var name = "http://www.microsoft.com";  
var xhrDiv = document.getElementById("xhrDiv");  
  
var req = new XMLHttpRequest();  
req.open("GET", name, true);  
req.responseType = "arraybuffer";  
req.onreadystatechange = function () {  
if (req.readyState == req.DONE) {  
    var arrayResponse = req.response;  
    var dataView = new DataView(arrayResponse);  
    var ints = new Uint32Array(dataView.byteLength / 4);  
  
    xhrDiv.style.backgroundColor = "#00FF00";  
    xhrDiv.innerText = "Array is " + ints.length + "uints long";  
    }  
}  
req.send();  
```  
  
## <a name="arraybuffer"></a>ArrayBuffer  
 Un [objeto ArrayBuffer](../../javascript/reference/arraybuffer-object.md) representa un búfer de datos sin procesar que se usa para almacenar datos para las diferentes matrices con tipo. No se puede leer de un objeto `ArrayBuffer` ni escribir en él, pero puede pasarlo a una matriz con tipo u [objeto DataView](../../javascript/reference/dataview-object.md) para interpretar el búfer sin procesar. Puede usar `ArrayBuffer` para almacenar cualquier tipo de datos (o tipos mixtos de datos).  
  
## <a name="dataview"></a>DataView  
 Puede usar el [objeto DataView](../../javascript/reference/dataview-object.md) para leer y escribir distintos tipos de datos binarios en cualquier ubicación del objeto `ArrayBuffer`.  
  
## <a name="typed-arrays"></a>Matrices con tipo  
 Los tipos de matriz con tipo representan vistas de un [objeto ArrayBuffer](../../javascript/reference/arraybuffer-object.md) que se pueden indexar y manipular. Todos los tipos de matriz son de longitud fija.  
  
||||  
|-|-|-|  
|Nombre|Tamaño (en bytes)|Descripción|  
|[Int8Array (Objeto)](../../javascript/reference/int8array-object.md)|1|Entero con signo del complemento a dos de ocho bits|  
|[Uint8Array (Objeto)](../../javascript/reference/uint8array-object.md)|1|Entero sin signo de ocho bits|  
|[Int16Array (Objeto)](../../javascript/reference/int16array-object.md)|2|Entero con signo del complemento a dos de dieciséis bits|  
|[Uint16Array (Objeto)](../../javascript/reference/uint16array-object.md)|2|Entero sin signo de dieciséis bits|  
|[Int32Array (Objeto)](../../javascript/reference/int32array-object.md)|4|Entero con signo del complemento a dos de treinta y dos bits|  
|[Uint32Array (Objeto)](../../javascript/reference/uint32array-object.md)|4|Entero sin signo de treinta y dos bits|  
|[Float32Array (Objeto)](../../javascript/reference/float32array-object.md)|4|Punto flotante IEEE de treinta y dos bits|  
|[Float64Array (Objeto)](../../javascript/reference/float64array-object.md)|8|Punto flotante IEEE de sesenta y cuatro bits|