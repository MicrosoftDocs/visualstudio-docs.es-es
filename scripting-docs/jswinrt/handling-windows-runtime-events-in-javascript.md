---
title: Control de eventos de Windows Runtime en JavaScript | Microsoft Docs
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
- JavaScript, Windows Runtime events
- Windows Runtime events [JavaScript]
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 29eb97427c2c5a29ee9a66e8e2a85953fd797efd
ms.openlocfilehash: e963472ee51f2439b50807a49425dcd7f6d8443a
ms.contentlocale: es-es
ms.lasthandoff: 08/11/2017

---
# <a name="handling-windows-runtime-events-in-javascript"></a>Control de eventos de Windows Runtime en JavaScript
Los eventos de Windows Runtime no se representan del mismo modo en JavaScript que en C++ o .NET Framework. No son propiedades de clase y se representan como identificadores de cadena que se pasan a los métodos `addEventListener` y `removeEventListener` de clase. Por ejemplo, puede agregar un controlador de eventos para el evento [Geolocator.PositionChanged](http://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) pasando la cadena "positionchanged" al método `Geolocator.addEventListener`:  
  
```JavaScript  
var locator =  new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 También puede establecer la propiedad `locator.onpositionchanged`.  
  
```  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
 En JavaScript, los argumentos de evento de Windows en tiempo de ejecución se representan como un único objeto de evento. En el ejemplo siguiente de un método de controlador de eventos, el parámetro `ev` es un objeto que contiene tanto el remitente (la propiedad de destino) como el resto de argumentos de evento. Los argumentos de evento son los que se documentan para cada evento.  
  
```JavaScript  
function (ev) {  
    console.log("Target: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
  
```  
  
> [!IMPORTANT]
>  Las características de Windows Runtime no están disponibles para las aplicaciones que se ejecutan en Internet Explorer.  
  
## <a name="see-also"></a>Vea también  
 [Uso de Windows Runtime en JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)
