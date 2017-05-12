---
title: "Usar m&#233;todos asincr&#243;nicos de Windows en tiempo de ejecuci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Métodos asincrónicos de Windows en tiempo de ejecución"
ms.assetid: 70756833-44f7-4383-827f-2ac781558082
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Usar m&#233;todos asincr&#243;nicos de Windows en tiempo de ejecuci&#243;n
Muchos de los métodos de Windows en tiempo de ejecución, en especial aquellos que requieren mucho tiempo para completarse, son asincrónicos.  Por lo general, son métodos que devuelven una operación o acción asincrónica \(por ejemplo, `Windows.Foundation.IAsyncAction`, `Windows.Foundation.IAsyncOperation`, `Windows.Foundation.IAsyncActionWithProgress` o `Windows.Foundation.IAsyncOperationWithProgress`\).  Estos métodos se representan en JavaScript con el patrón [CommonJS\/Promises\/A](http://go.microsoft.com/fwlink/p/?LinkId=244434).  Es decir, devuelven un objeto Promise que tiene una función [then](http://msdn.microsoft.com/es-es/c63904fc-465b-4fd5-a1d6-e4fb200248e7), para la cual debe proporcionarse una función `completed` que controle el resultado si la operación finaliza con éxito.  Si no desea proporcionar un controlador de errores, use la función [done](http://msdn.microsoft.com/es-es/9a5e6877-a2cf-421f-a91e-37d84ccb40da) en vez de la función [then](http://msdn.microsoft.com/es-es/c63904fc-465b-4fd5-a1d6-e4fb200248e7).  
  
> [!IMPORTANT]
>  Las características de Windows en tiempo de ejecución no están disponibles para las aplicaciones que se ejecutan en Internet Explorer.  
  
## Ejemplos de métodos asincrónicos  
 En el ejemplo siguiente, la función [then](http://msdn.microsoft.com/es-es/c63904fc-465b-4fd5-a1d6-e4fb200248e7) toma un parámetro que representa el valor completado del método `createResourceAsync`.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
        console.log("New item is: " + newItem.id);  
            });  
```  
  
 En este caso, si el método `createResourceAsync` da error, devuelve una promesa en el estado de error, pero no genera una excepción.  El error se puede administrar con la función [then](http://msdn.microsoft.com/es-es/c63904fc-465b-4fd5-a1d6-e4fb200248e7) del modo siguiente.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
              console.log("New item is: " + newItem.id);  
          }  
          function(err) {  
              console.log("Got error: " + err.message);  
          });  
```  
  
 Si no quiere administrar el error de forma explícita, pero desea que genere una excepción, puede usar la función [done](http://msdn.microsoft.com/es-es/9a5e6877-a2cf-421f-a91e-37d84ccb40da) en su lugar.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .done(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            });  
```  
  
 También puede mostrar el desarrollo con una tercera función.  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .then(function(newItem) {   
               console.log("New item is: " + newItem.id);  
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
  
 Para obtener más información sobre programación asincrónica, vea [Asynchronous programming](http://msdn.microsoft.com/es-es/904ff97c-bb36-4ac5-9eda-a961e3639415).  
  
## Vea también  
 [Utilizar Windows en tiempo de ejecución en JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)