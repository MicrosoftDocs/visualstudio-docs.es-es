---
title: "&lt;deprecated&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;deprecated&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica una función o un método desusado.  
  
## Sintaxis  
  
```  
<deprecated  
    type="deprecate|remove"  
    locid="descriptionID">description  
</deprecated>  
```  
  
#### Parámetros  
 `type`  
 Opcional.  Especifica si la función o el método se quitará en futuras versiones, o si la función o el método ya se ha quitado y su uso puede producir un error.  Establézcalo en `deprecate` para especificar que la función o el método se quitará en futuras versiones.  Establézcalo en `remove` para especificar que la función o el método ya se ha quitado.  
  
 `locid`  
 Opcional.  Identificador de la información de localización sobre la función o el método.  El identificador es un identificador de miembro o corresponde al valor del atributo `name` en un paquete de mensajes definido por los metadatos de OpenAjax.  El tipo de identificador depende del formato especificado en el elemento [\<loc\>](../ide/loc-javascript.md).  
  
 `description`  
 Opcional.  Descripción de la función o el método que se va a desusar.  
  
## Comentarios  
 Los elementos utilizados para anotar funciones, entre los que se incluye `<deprecated>`, se deben colocar en el cuerpo de la función antes de cualquier instrucción.  Al marcar una función como desusada, se recomienda reemplazar su elemento [\<summary\>](../ide/summary-javascript.md) con el elemento `<deprecated>`.  
  
## Ejemplo  
 En el código siguiente se muestra cómo usar el elemento `<deprecated>`.  
  
```javascript  
function areaFunction(radiusParam) {  
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## Vea también  
 [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md)