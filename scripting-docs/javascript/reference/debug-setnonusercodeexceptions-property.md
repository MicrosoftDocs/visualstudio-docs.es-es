---
title: "Debug.setNonUserCodeExceptions (Propiedad) | Microsoft Docs"
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
ms.assetid: 1dd2abee-a415-41bb-a359-017da62f9485
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Debug.setNonUserCodeExceptions (Propiedad)
Determina si el depurador debe tratar como no controlados por el usuario algunos de los bloques try\-catch de este ámbito.  Las excepciones se pueden clasificar como producidas, no controladas por el usuario o no controladas a secas.  
  
 Si esta propiedad se establece en `true` en un ámbito determinado, el depurador puede realizar alguna acción \(por ejemplo, interrumpir\) con las excepciones que se produzcan dentro de él si el programador quiere interrumpir las excepciones no controladas por el usuario.  Si esta propiedad se establece en `false`, es igual que si no se hubiera establecido.  
  
 Para obtener más información acerca de la depuración, vea [Información general acerca de la depuración de Active Script](http://go.microsoft.com/fwlink/p/?LinkId=249469).  
  
## Sintaxis  
  
```  
Debug.setNonUserCodeExceptions [= bool];  
```  
  
## Ejemplo  
 El código siguiente muestra cómo establecer esta propiedad.  
  
```javascript  
(function () {  
    Debug.setNonUserCodeExceptions = true;  
    try{  
        var x = null;  
        x.y();  
    } catch (e) {  
    // Catch the exception.  
    }  
})();  
```  
  
## Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]