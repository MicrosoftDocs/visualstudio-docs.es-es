---
title: El URI que se desea descodificar no es una codificación válida | Documentos de Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fd8add72d016bc3f2e815f41c29c735505c8817
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108430"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>El URI que se desea descodificar no tiene una codificación válida
Se intentó descodificar un identificador URI formado incorrectamente (identificador uniforme de recursos). Los identificadores URI tienen una sintaxis especial; mayoría de los caracteres no alfanuméricos debe codificarse antes de que se pueden usar en un URI. Puede usar el `encodeURI` y `encodeURIComponent` métodos para crear un URI de una normal [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] cadena.  
  
 Un URI completo se compone de una secuencia de componentes y los separadores. El formato general es:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Los nombres de los corchetes angulares representan los componentes y el ":", "/", ";" y "?" son caracteres reservados que se usan como separadores.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de que intenta descodificar a identificadores URI válidos solo. No se puede descodificar normal [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] cadenas, ya que pueden contener caracteres no válidos.  
  
## <a name="see-also"></a>Vea también  
 [decodeURI (función)](../../javascript/reference/decodeuri-function-javascript.md)   
 [DecodeURIComponent (Función)](../../javascript/reference/decodeuricomponent-function-javascript.md)