---
title: Utilizar el método bind (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bind method [JavaScript]
- this object [JavaScript]
ms.assetid: f608f95b-3b9d-437a-a67a-5a4ef8f6c07f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d185801cc5bba355751147edb79b9c47d21f8eed
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2018
ms.locfileid: "28987872"
---
# <a name="using-the-bind-method-javascript"></a>Utilizar el método bind (JavaScript)
El método `bind` de JavaScript se puede usar de varias formas. Normalmente, se utiliza para conservar el contexto de ejecución para una función que se ejecuta en otro contexto. `bind` crea una nueva función con el mismo cuerpo que la función original. El primer argumento que se pasa a `bind` especifica el valor de palabra clave `this` en la función enlazada. También puede pasar más argumentos opcionales a `bind`. Para ver ejemplos de otros usos, consulte el [Método bind (Función)](../../javascript/reference/bind-method-function-javascript.md). Para obtener un ejemplo sobre cómo usar `bind` para aplicar funciones parcialmente, consulte [Patrones de programación asincrónica y sugerencias en Hilo JavaScript (Microsoft Store)](http://msdn.microsoft.com/library/windows/apps/jj649740.aspx).  
  
## <a name="preserving-the-execution-context-using-bind"></a>Conservar el contexto de ejecución mediante bind  
 La función `bind` se suele utilizar al agregar agentes de escucha de eventos. En el ejemplo de código siguiente, `bind` se utiliza para conservar el contexto del objeto actual (`DataObject`). El objeto de datos se pasa a `bind` mediante la palabra clave `this`, que proporciona acceso a las funciones y propiedades del objeto de datos cuando se ejecuta el controlador de eventos (`dataReadyHandler`). Para mostrar cómo funciona `bind`, este código crea un evento personalizado.  
  
```JavaScript  
var data;  
  
var dataReadyEvent = document.createEvent("Event");  
dataReadyEvent.initEvent("dataReady", true, false);  
  
function DataObject() {  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReadyHandler;  
    document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
    // To see the result of not using bind, comment out the preceding line,   
    // and uncomment the following line of code.  
    // document.addEventListener('dataReady', this.onDataCompleted);  
}  
function dataReadyHandler() {  
    if (console && console.log) {  
        console.log("Data object property value: " + this.name);  
        console.log("Data object property value: " + this.data());  
    }  
}  
  
setTimeout(function () {  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
    }, 5000);
  
var dataObj = new DataObject();  
  
// Output:  
// Data Object  
// 0,1,2,3  
  
```  
  
 Si convierte en comentario la línea de código que utiliza `bind`, quita los comentarios de la línea de código que llama a `addEventListener` sin `bind` y después vuelve a ejecutar el código, la función `dataReadyHandler` genera un error. Por ejemplo, en `dataReadyHandler`, `this.name` quedará sin definir, y `this.data()` producirá un error porque el objeto `this` ya no hace referencia al objeto de datos.  
  
## <a name="see-also"></a>Vea también  
 [bind (Método, Function)](../../javascript/reference/bind-method-function-javascript.md)
