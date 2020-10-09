---
title: El URI que se va a codificar contiene un carácter no válido | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 310db785041de0beb0ebbba0cdd9b7c356397bc4
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862383"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>El URI que se desea codificar contiene un carácter no válido
Ha intentado codificar una cadena como un URI (identificador uniforme de recursos), pero contiene caracteres no válidos. Aunque la mayoría de los caracteres son válidos dentro de las cadenas que se van a convertir en URI, algunas secuencias de caracteres Unicode no son válidas.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de que la cadena que se va a codificar contiene solo secuencias Unicode válidas. Un URI completo se compone de una secuencia de componentes y separadores. Los nombres entre corchetes angulares representan componentes y los caracteres ":", "/", ";" y "?" son caracteres reservados que se usan como separadores. El formato general es:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Vea también  
 [encodeURI (función)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeuri)   
 [encodeURIComponent (Función)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeuricomponent)