---
title: "ArrayBuffer (Objeto) | Microsoft Docs"
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
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# ArrayBuffer (Objeto)
Representa un búfer de datos binarios sin formato que se usa para almacenar datos para las diferentes matrices con tipo.  `ArrayBuffers` No se puede leer ni escribir en él de forma directa, pero puede pasarse a una matriz con tipo o un objeto [DataView \(Objeto\)](../../javascript/reference/dataview-object.md) para interpretar el búfer sin formato según sea necesario.  
  
 Para obtener más información sobre las matrices con tipo, consulte [Matrices con tipo](../../javascript/advanced/typed-arrays-javascript.md).  
  
## Sintaxis  
  
```javascript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## Parámetros  
 `arrayBuffer`  
 Requerido.  Nombre de variable a la que se asigna el objeto `ArrayBuffer`.  
  
 `length`  
 Longitud del búfer.  El contenido del objeto ArrayBuffer se inicializa en 0.  Si el número de bytes solicitado no se puede asignar, se produce una excepción.  
  
## Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `ArrayBuffer`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[byteLength \(Propiedad\)](../../javascript/reference/bytelength-property-arraybuffer.md)|Sólo lectura.  Longitud del objeto ArrayBuffer en bytes.|  
  
## Funciones  
 En la tabla siguiente se muestran las funciones del objeto `ArrayBuffer`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[ArrayBuffer.isView \(Función\)](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|Determina si un objeto permite ver el búfer.|  
  
## Métodos  
 En la tabla siguiente se muestran los métodos del objeto `ArrayBuffer`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[slice \(Método\)](../../javascript/reference/slice-method-arraybuffer.md)|Devuelve una sección de `ArrayBuffer`.|  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo usar un objeto ArrayBuffer para procesar los datos binarios adquiridos de [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx).  Puede usar [DataView \(Objeto\)](../../javascript/reference/dataview-object.md) para obtener cada valor.  
  
```javascript  
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
  
## Comentarios  
 Para obtener más información acerca de cómo usar `XmlHttpRequest`, vea [XMLHttpRequest enhancements](http://msdn.microsoft.com/es-es/be09137c-6546-441b-b953-dcbf72b77069).  
  
## Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]