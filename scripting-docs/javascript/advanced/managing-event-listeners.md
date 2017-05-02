---
title: "Administrar agentes de escucha de eventos | Microsoft Docs"
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
ms.assetid: 87717f5d-b0c6-4c8d-a293-476002b7bfcf
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Administrar agentes de escucha de eventos
Si la duración de un objeto o elemento DOM no es igual que la de su agente de escucha de eventos asociado, podría ser necesario usar el método [removeEventListener](http://msdn.microsoft.com/library/ie/ff975250\(v=vs.85\).aspx) para evitar pérdidas de memoria.  
  
## Agentes de escucha de eventos y ámbito de objetos  
 En el siguiente ejemplo de código se muestra código que podría dar lugar a una pérdida de memoria al llamar a la función `dataObjFactory()`.  En este código, se registra un agente de escucha de eventos para un objeto de datos cada vez que se crea un objeto de datos nuevo.  Para que el objeto de datos actual esté disponible en el controlador de eventos `dataReady()`, se usa [bind \(Método, Function\)](../../javascript/reference/bind-method-function-javascript.md) en `addEventListener`.  
  
```javascript  
 var data;  
 var dataObj;  
  
 var dataReadyEvent = document.createEvent("Event");  
 dataReadyEvent.initEvent("dataReady", true, false);  
  
 function DataObject() {  
  
     this.name = "Data Object";  
     this.data = function () {  
         return data;  
     }  
     this.onDataCompleted = dataReady;  
     // this.handlerRef = this.onDataCompleted.bind(this);  
  
     // document.addEventListener('dataReady', this.handlerRef);  
     document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
 }  
  
 // Runs when the data is available.  
 function dataReady() {  
     if (console && console.log) {  
         console.log("object value: " + this.name);  
         console.log("object value: " + this.data());  
     }  
 }  
  
setTimeout(function () {  
    // Generate data after a timeout period.  
    data = [0, 1, 2, 3];  
    document.dispatchEvent(dataReadyEvent);  
}, 10000);  
  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             // The following line of code has no effect.  
             document.removeEventListener('dataReady', dataObj.onDataCompleted);  
             dataObj = null;  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
 dataObjFactory();  
```  
  
 El agente de escucha de cada objeto de datos se registra con el objeto `document`, que tiene una duración distinta a la de los objetos de datos.  El agente de escucha de eventos de cada objeto de datos impide que este se recolecte siempre que el objeto `document` permanezca en el ámbito.  \(En algunos patrones de diseño JavaScript modernos, el objeto de documento permanece en el ámbito mientras dura la aplicación web.\) Para impedir una pérdida de memoria, se llama a `removeEventListener` en la función `dataObjFactory`.  Con todo, este código produce un error porque no se ha llamado a `removeEventListener` en la versión enlazada del controlador de eventos que la función `bind` devuelve.  
  
 Para corregir este código y que los objetos de datos estén disponibles para su recolección, primero debe almacenar una referencia a la versión enlazada del controlador de eventos, como se muestra en este código, y, a continuación, pasar dicha referencia a `addEventListener`.  El código corregido para `DataObject` es:  
  
```javascript  
function DataObject() {  
  
    this.name = "Data Object";  
    this.data = function () {  
        return data;  
    }  
    this.onDataCompleted = dataReady;  
    this.handlerRef = this.onDataCompleted.bind(this);  
  
    document.addEventListener('dataReady', this.handlerRef);  
    // document.addEventListener('dataReady', this.onDataCompleted.bind(this));  
}  
  
```  
  
 Por último, debe llamar a `removeEventListener` en la referencia almacenada \(`handlerRef`\) de la función enlazada.  El código corregido para `dataObjFactory` es:  
  
```javascript  
function dataObjFactory() {  
     for (var x = 0; x < 100; x++) {  
         if (dataObj) {  
             document.removeEventListener('dataReady', dataObj.handlerRef);  
         }  
         dataObj = new DataObject();  
     }  
 }  
  
```  
  
 Así, la llamada a `removeEventListener` funciona y los objetos de datos innecesarios se pueden recopilar incluso si el objeto `document` sigue estando en el ámbito.