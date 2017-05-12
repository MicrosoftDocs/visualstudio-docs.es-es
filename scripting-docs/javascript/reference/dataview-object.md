---
title: "DataView (Objeto) | Microsoft Docs"
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
ms.assetid: 250ec067-7505-4ee0-82ab-bfd3c2820afa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# DataView (Objeto)
Puede usar un objeto DataView para leer y escribir los diferentes tipos de datos binarios en cualquier ubicación de ArrayBuffer.  
  
## Sintaxis  
  
```  
  
dataView = new DataView(buffer, byteOffset, byteLength);  
```  
  
## Parámetros  
 `dataView`  
 Requerido.  Nombre de variable al que se asigna el objeto **DataView**.  
  
 `buffer`  
 ArrayBuffer que el objeto DataView representa.  
  
 `byteOffset`  
 Opcional.  Especifica el desplazamiento en bytes desde el principio del búfer donde debe empezar el objeto DataView.  
  
 `byteLength`  
 Opcional.  Especifica la longitud \(en bytes\) de la sección del búfer que el objeto DataView debe representar.  
  
## Comentarios  
 Si se omiten byteOffset y byteLength, el objeto DataView abarca el intervalo completo de ArrayBuffer.  Si se omite byteLength, el objeto DataView se extiende desde el valor de byteOffset especificado hasta el final de ArrayBuffer.  Si los valores especificados de byteOffset y byteLength hacen referencia a un área situada más allá del final de ArrayBuffer, se produce una excepción.  
  
## Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `DataView`.  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[buffer \(Propiedad\)](../../javascript/reference/buffer-property-dataview.md)|Es de solo lectura.  Obtiene el ArrayBuffer al que hace referencia esta vista.|  
|[byteLength \(Propiedad\)](../../javascript/reference/bytelength-property-dataview.md)|Es de solo lectura.  Longitud de esta vista desde el principio de su ArrayBuffer, en bytes, corregida en el momento de la construcción.|  
|[byteOffset \(Propiedad\)](../../javascript/reference/byteoffset-property-dataview.md)|Es de solo lectura.  El desplazamiento de esta vista desde el principio de su ArrayBuffer, en bytes, corregido en el momento de la construcción.|  
  
## Métodos  
 En la tabla siguiente se muestran los métodos del objeto `DataView`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[getInt8 \(Método\)](../../javascript/reference/getint8-method-dataview.md)|Obtiene el valor Int8 en el desplazamiento de bytes especificado desde el inicio de la vista.|  
|[getUint8 \(Método, DataView\)](../../javascript/reference/getuint8-method-dataview.md)|Obtiene el valor Uint8 en el desplazamiento de bytes especificado desde el inicio de la vista.|  
|[getInt16 \(Método, DataView\)](../../javascript/reference/getint16-method-dataview.md)|Obtiene el valor Int16 en el desplazamiento de bytes especificado desde el inicio de la vista.|  
|[getUint16 \(Método, DataView\)](../../javascript/reference/getuint16-method-dataview.md)|Obtiene el valor Uint16 en el desplazamiento de bytes especificado desde el inicio de la vista.|  
|[getInt32 \(Método, DataView\)](../../javascript/reference/getint32-method-dataview.md)|Obtiene el valor Int32 en el desplazamiento de bytes especificado desde el inicio de la vista.|  
|[getUint32 \(Método, DataView\)](../../javascript/reference/getuint32-method-dataview.md)|Obtiene el valor Uint32 en el desplazamiento de bytes especificado desde el inicio de la vista.|  
|[getFloat32 \(Método, DataView\)](../../javascript/reference/getfloat32-method-dataview.md)|Obtiene el valor Float32 en el desplazamiento de bytes especificado desde el inicio de la vista.|  
|[getFloat64 \(Método, DataView\)](../../javascript/reference/getfloat64-method-dataview.md)|Obtiene el valor Float64 en el desplazamiento de bytes especificado desde el inicio de la vista.|  
|[setInt8 \(Método, DataView\)](../../javascript/reference/setint8-method-dataview.md)|Almacena un valor Int8 en el desplazamiento de bytes especificado desde el inicio de la vista.|  
|[setUint8 \(Método, DataView\)](../../javascript/reference/setuint8-method-dataview.md)|Almacena un valor Uint8 en el desplazamiento de bytes especificado desde el inicio de la vista.|  
|[setInt16 \(Método, DataView\)](../../javascript/reference/setint16-method-dataview.md)|Almacena un valor Int16 en el desplazamiento de bytes especificado desde el inicio de la vista.|  
|[setUint16 \(Método, DataView\)](../../javascript/reference/setuint16-method-dataview.md)|Almacena un valor Uint16 en el desplazamiento de bytes especificado desde el inicio de la vista.|  
|[setInt32 \(Método, DataView\)](../../javascript/reference/setint32-method-dataview.md)|Almacena un valor Int32 en el desplazamiento de bytes especificado desde el inicio de la vista.|  
|[setUint32 \(Método, DataView\)](../../javascript/reference/setuint32-method-dataview.md)|Almacena un valor Uint32 en el desplazamiento de bytes especificado desde el inicio de la vista.|  
|[setFloat32 \(Método, DataView\)](../../javascript/reference/setfloat32-method-dataview.md)|Almacena un valor Float32 en el desplazamiento de bytes especificado desde el inicio de la vista.|  
|[setFloat64 \(Método, DataView\)](../../javascript/reference/setfloat64-method-dataview.md)|Almacena un valor Float64 en el desplazamiento de bytes especificado desde el inicio de la vista.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo usar un objeto DataView para procesar los datos binarios adquiridos de un XmlHttpRequest:  
  
```javascript  
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
  
## Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]