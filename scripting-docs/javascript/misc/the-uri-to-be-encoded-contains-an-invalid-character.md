---
title: El URI que se desea codificar contiene un carácter no válido | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e93d145ea6b0991123c2a7c80f8acf54a83a264
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24632935"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>El URI que se desea codificar contiene un carácter no válido
Ha intentado codificar una cadena como un URI (Uniform Resource Identifier), pero contiene caracteres no válidos. Aunque la mayoría de los caracteres es válida dentro de las cadenas se convierta en URI, algunas secuencias de caracteres Unicode no son válidas.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Asegúrese de que la cadena que se desea codificar contiene solo las secuencias de Unicode válidas. Un URI completo se compone de una secuencia de componentes y separadores. Los nombres de los corchetes angulares representan componentes y el ":", "/", ";" y "?" son caracteres reservados utilizados como separadores. La forma general es:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Vea también  
 [encodeURI (función)](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent (Función)](../../javascript/reference/encodeuricomponent-function-javascript.md)