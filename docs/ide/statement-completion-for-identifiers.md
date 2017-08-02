---
title: "Finalizaci&#243;n de instrucciones para identificadores | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense [JavaScript], finalización de instrucciones"
  - "finalización de instrucciones, IntelliSense para JavaScript"
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Finalizaci&#243;n de instrucciones para identificadores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

JavaScript no permite explícita escribiendo para las declaraciones de variables.  En consecuencia, IntelliSense no puede proporcionar siempre las listas de finalización para los objetos.  Esto puede ocurrir en varias situaciones.  Siguientes son algunos de los más utilizados.  
  
-   Se declara un parámetro, pero aún no se ha llamado en otro lugar del documento activo, tal como se muestra en el ejemplo siguiente.  
  
    ```javascript  
    function illuminate(light) {  
             light.  // Accurate statement completion is not available   
                     // unless illuminate is called elsewhere with a   
                     // parameter that has a value. If it is called only  
                     // in a function that is a sibling to   
                     // illuminate(light) in the call hierarchy, the   
                     // IntelliSense engine also cannot determine the   
                     // parameter type.  
         }  
  
    // Sibling function. No statement completion for light   
    // object in preceding code.  
    function lightLamp() {  
        var x = illuminate(1);  
    }  
  
    // Uncomment the next line to obtain statement completion for  
    // light object in preceding code.  
    // var x = illuminate(1);  
    ```  
  
-   Un objeto está en una función que se llama en respuesta a un evento.  En tiempo de diseño, el motor de IntelliSense no puede determinar el tipo de los objetos utilizados en esta situación.  
  
     Si el motor de IntelliSense puede determinar que el evento se debe llamar, normalmente mediante el uso de `addEventListener` para el evento en el documento activo, se proporciona información más precisa de IntelliSense.  
  
 Cuando IntelliSense es capaz de identificar un objeto, el motor de IntelliSense llena la lista de finalización con entidades con nombre o los identificadores que están presentes en el documento activo.  Cuando la lista de finalización contiene estos identificadores, aparecen iconos de información junto a ellos.  Además, una información sobre herramientas para cada identificador indica que la expresión es desconocida.  La ilustración siguiente muestra las opciones de finalización de un objeto de tipo de instrucción `light` que no se puede identificar porque el objeto y sus propiedades no están definidas.  Sin embargo, la `intensity` propiedad está disponible en la lista de identificador porque se ha utilizado en el `illuminate` función.  
  
 **Opciones de finalización de un objeto que no se puede identificar**  
  
 ![IntelliSense para JavaScript para identificadores](~/docs/ide/media/js_intellisense_identifiers.png "js\_intellisense\_identifiers")  
  
 Puede reemplazar la lista de finalización de un objeto mediante el uso de comentarios de documentación XML o las características de extensibilidad de IntelliSense de JavaScript.  Con estas características, puede proporcionar información de tipo e información de IntelliSense más descriptiva cuando no es posible que de lo contrario disponerse.  Para obtener más información, vea [Extender IntelliSense para JavaScript](../ide/extending-javascript-intellisense.md) y [Cómo: Crear comentarios de documentación XML de JavaScript](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).  
  
## Vea también  
 [IntelliSense para JavaScript](../ide/javascript-intellisense.md)