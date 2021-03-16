---
description: Ha intentado descodificar un URI formado incorrectamente.
title: El URI que se va a descodificar no es una codificación válida | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: db9d2f89a193ca4542ff5d1ca5ed5c2ae6419f53
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571992"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>El URI que se desea descodificar no tiene una codificación válida
Ha intentado descodificar un URI formado incorrectamente (identificador uniforme de recursos). Los URI tienen una sintaxis especial; la mayoría de los caracteres no alfanuméricos se deben codificar antes de que se puedan usar en un URI. Puede usar los `encodeURI` métodos y `encodeURIComponent` para crear un URI a partir de una [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] cadena normal.  
  
 Un URI completo se compone de una secuencia de componentes y separadores. El formato general es:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Los nombres entre corchetes angulares representan componentes y los caracteres ":", "/", ";" y "?" son caracteres reservados que se usan como separadores.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de que está intentando descodificar solo los URI válidos. No se pueden descodificar [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] cadenas normales, ya que pueden contener caracteres no válidos.  
  
## <a name="see-also"></a>Consulte también  
 [decodeURI (función)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuri)   
 [decodeURIComponent (función)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuricomponent)
