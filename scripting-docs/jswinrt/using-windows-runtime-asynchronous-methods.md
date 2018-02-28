---
title: "Uso de métodos asincrónicos de Windows Runtime | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime asynchronous methods
ms.assetid: 70756833-44f7-4383-827f-2ac781558082
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 215a04a2f3f875743a7fbf910a3a565cf34fb558
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="using-windows-runtime-asynchronous-methods"></a>Uso de métodos asincrónicos de Windows Runtime
Muchos de los métodos de Windows Runtime, en especial aquellos que requieren mucho tiempo para completarse, son asincrónicos. Por lo general, son métodos que devuelven una operación o acción asincrónica (por ejemplo, `Windows.Foundation.IAsyncAction`, `Windows.Foundation.IAsyncOperation`, `Windows.Foundation.IAsyncActionWithProgress` o `Windows.Foundation.IAsyncOperationWithProgress`). Estos métodos se representan en JavaScript mediante el patrón [CommonJS/Promises/A](http://go.microsoft.com/fwlink/p/?LinkId=244434). Es decir, devuelven un objeto Promise que tiene una función [then](https://msdn.microsoft.com/en-us/library/windows/apps/br229728.aspx), para la cual debe proporcionarse una función `completed` que controle el resultado si la operación finaliza con éxito. Si no desea proporcionar un controlador de errores, use la función [done](https://msdn.microsoft.com/en-us/library/windows/apps/hh701079.aspx) en vez de la función `then`.  
  
> [!IMPORTANT]
>  Las características de Windows Runtime no están disponibles para las aplicaciones que se ejecutan en Internet Explorer.  
  
## <a name="examples-of-asynchronous-methods"></a>Ejemplos de métodos asincrónicos  
 En el ejemplo siguiente, la función `then` toma un parámetro que representa el valor completado del método `createResourceAsync`.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
        console.log("New item is: " + newItem.id);  
            });  
```  
  
 En este caso, si el método `createResourceAsync` da error, devuelve una promesa en el estado de error, pero no genera una excepción. El error se puede administrar con la función `then` del modo siguiente.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
              console.log("New item is: " + newItem.id);  
          }  
          function(err) {  
              console.log("Got error: " + err.message);  
          });  
```  
  
 Si no quiere administrar el error de forma explícita, pero desea que genere una excepción, puede usar la función `done` en su lugar.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .done(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            });  
```  
  
 También puede mostrar el desarrollo con una tercera función.  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .then(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            },  
    // Error.  
            function(error) {   
               alert("Failed to create a resource.");  
            },  
    // Progress.  
            function(progress, resultSoFar) {   
               setProgressBar(progress);  
            });  
```  
  
 Para obtener más información sobre la programación asincrónica, consulte [Programación asincrónica en JavaScript](https://msdn.microsoft.com/en-us/library/windows/apps/hh700330.aspx).  
  
## <a name="see-also"></a>Vea también  
 [Uso de Windows Runtime en JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)