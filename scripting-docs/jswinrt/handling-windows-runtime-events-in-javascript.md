---
title: Control de eventos de Windows Runtime en JavaScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime events
- Windows Runtime events [JavaScript]
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7e5780a2462e8980c22c474ae6236c87aee599b
ms.sourcegitcommit: 498e39e89a89ad7bf9dcb0617424fff999b1c3b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/21/2018
ms.locfileid: "36302819"
---
# <a name="handling-windows-runtime-events-in-javascript"></a>Control de eventos de Windows Runtime en JavaScript
Los eventos de Windows Runtime no se representan del mismo modo en JavaScript que en C++ o .NET Framework. No son propiedades de clase y se representan como identificadores de cadena (en minúscula) que se pasan a los métodos `addEventListener` y `removeEventListener` de clase. Por ejemplo, puede agregar un controlador de eventos para el evento [Geolocator.PositionChanged](https://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) pasando la cadena "positionchanged" al método `Geolocator.addEventListener`:  
  
```JavaScript  
var locator = new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 También puede establecer la propiedad `locator.onpositionchanged`:  
  
```JavaScript  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
Otra diferencia entre .NET/C++ y JavaScript es el número de parámetros que utiliza el controlador de eventos. En .NET o C++, el controlador utiliza dos: el remitente del evento y los datos del evento. En JavaScript, los dos se agrupan como un único objeto `Event`. En el ejemplo siguiente, el parámetro `ev` contiene tanto el remitente del evento (la propiedad `target`) y las propiedades de datos del evento (en este caso, simplemente `position`). Las propiedades de datos del evento son las que se documentan para cada evento.
  
```JavaScript  
function (ev) {  
    console.log("Sender: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
```  
  
> [!IMPORTANT]
>  Las características de Windows en tiempo de ejecución no están disponibles para las aplicaciones que se ejecutan en Internet Explorer.  
  
## <a name="see-also"></a>Vea también  
 [Uso de Windows Runtime en JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)
