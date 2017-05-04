---
title: "Matrices con tipo (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: fa82c562-0ebf-4559-aecc-166e59f7fb64
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Matrices con tipo (JavaScript)
Puede usar matrices con tipo para controlar datos binarios de orígenes como protocolos de red, formatos de archivo binario y búferes de gráficos sin procesar.  Las matrices con tipo también pueden usarse para administrar datos binarios en memoria con diseños de byte conocidos.  
  
## Ejemplo  
 En el código siguiente se muestra cómo usar un [ArrayBuffer \(Objeto\)](../../javascript/reference/arraybuffer-object.md) como respuesta de [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx).  Puede manipular los bytes de la respuesta usando los distintos métodos del [DataView \(Objeto\)](../../javascript/reference/dataview-object.md) o copiando los bytes en la matriz con tipo correspondiente.  
  
> [!TIP]
>  Para obtener más información sobre el uso de los diferentes tipos de respuestas con `XmlHttpRequest`, consulte [XMLHttpRequest.responseType](http://msdn.microsoft.com/es-es/8d7738d1-4bfd-4cf1-8015-174def089556), [Mejoras de XMLHttpRequest](http://msdn.microsoft.com/es-es/be09137c-6546-441b-b953-dcbf72b77069) y [Descargar diferentes tipos de contenido \(aplicaciones de la Tienda Windows\)](http://msdn.microsoft.com/es-es/c0006bbd-17f9-4c6a-af81-2acaf109111d).  
  
```javascript  
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
  
## ArrayBuffer  
 Un [ArrayBuffer \(Objeto\)](../../javascript/reference/arraybuffer-object.md) representa un búfer de datos sin formato que se usa para almacenar datos para las diferentes matrices con tipo.  No se puede leer de un `ArrayBuffer` o escribir en él, pero puede pasarlo a una matriz con tipo o [DataView \(Objeto\)](../../javascript/reference/dataview-object.md) para interpretar el búfer sin formato.  Puede usar `ArrayBuffer` para almacenar cualquier tipo de datos \(o tipos mixtos de datos\).  
  
## DataView  
 Puede usar el [DataView \(Objeto\)](../../javascript/reference/dataview-object.md) para leer y escribir distintos tipos de datos binarios en cualquier ubicación de `ArrayBuffer`.  
  
## Matrices con tipo  
 Los tipos de matriz con tipo representan vistas de un [ArrayBuffer \(Objeto\)](../../javascript/reference/arraybuffer-object.md) que se pueden indexar y manipular.  Todos los tipos de matriz son de longitud fija.  
  
||||  
|-|-|-|  
|Nombre|Tamaño \(en bytes\)|Descripción|  
|[Int8Array \(Objeto\)](../../javascript/reference/int8array-object.md)|1|Entero con signo del complemento a dos de ocho bits|  
|[Uint8Array \(Objeto\)](../../javascript/reference/uint8array-object.md)|1|Entero sin signo de ocho bits|  
|[Int16Array \(Objeto\)](../../javascript/reference/int16array-object.md)|2|Entero con signo del complemento a dos de dieciséis bits|  
|[Uint16Array \(Objeto\)](../../javascript/reference/uint16array-object.md)|2|Entero sin signo de dieciséis bits|  
|[Int32Array \(Objeto\)](../../javascript/reference/int32array-object.md)|4|Entero con signo del complemento a dos de treinta y dos bits|  
|[Uint32Array \(Objeto\)](../../javascript/reference/uint32array-object.md)|4|Entero sin signo de treinta y dos bits|  
|[Float32Array \(Objeto\)](../../javascript/reference/float32array-object.md)|4|Punto flotante IEEE de treinta y dos bits|  
|[Float64Array \(Objeto\)](../../javascript/reference/float64array-object.md)|8|Punto flotante IEEE de sesenta y cuatro bits|