---
title: "&lt;summary&gt; (JavaScript) | Microsoft Docs"
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
  - "summary (etiqueta XML) [JavaScript]"
  - "etiqueta XML de JavaScript <summary>"
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;summary&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica la descripción de una función o un método.  
  
## Sintaxis  
  
```  
<summary locid="descriptionID">description  
</summary>  
```  
  
#### Parámetros  
 `locid`  
 Opcional.  Identificador de la información de localización sobre la función o el método.  El identificador es un identificador de miembro o corresponde al valor del atributo `name` en un paquete de mensajes definido por los metadatos de OpenAjax.  El tipo de identificador depende del formato especificado en el elemento [\<loc\>](../ide/loc-javascript.md).  
  
 `description`  
 Opcional.  Descripción de la función o el método.  
  
## Comentarios  
 Los elementos utilizados para anotar funciones, entre los que se incluyen [\<summary\>](../ide/summary-javascript.md), [\<param\>](../ide/param-javascript.md) y [\<returns\>](../ide/returns-javascript.md), se deben colocar en el cuerpo de la función antes de cualquier instrucción.  
  
## Ejemplo  
 En el código siguiente se muestra cómo usar el elemento `<summary>`.  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## Vea también  
 [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md)