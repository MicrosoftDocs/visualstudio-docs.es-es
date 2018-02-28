---
title: "El URI que se desea descodificar no tiene una codificación válida | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d37ca55dfd701aaeba2af729511a5ae6a4fa5f4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>El URI que se desea descodificar no tiene una codificación válida
Se intentó descodificar un formato incorrecto URI (Uniform Resource Identifier). Identificadores URI tienen una sintaxis especial; mayoría de los caracteres no alfanuméricos debe codificarse antes de que se puedan utilizar en un URI. Puede usar el `encodeURI` y `encodeURIComponent` métodos para crear un URI de una normal [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] cadena.  
  
 Un URI completo se compone de una secuencia de componentes y separadores. La forma general es:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Los nombres de los corchetes angulares representan componentes y el ":", "/", ";" y "?" son caracteres reservados utilizados como separadores.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Asegúrese de que está intentando descodificar a identificadores URI válidos solo. No se puede descodificar normal [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] cadenas, ya que pueden contener caracteres no válidos.  
  
## <a name="see-also"></a>Vea también  
 [decodeURI (función)](../../javascript/reference/decodeuri-function-javascript.md)   
 [DecodeURIComponent (Función)](../../javascript/reference/decodeuricomponent-function-javascript.md)