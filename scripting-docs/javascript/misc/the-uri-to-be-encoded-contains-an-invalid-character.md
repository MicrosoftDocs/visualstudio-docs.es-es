---
title: El URI que se desea codificar contiene un carácter no válido | Documentos de Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: f2f9111acf656bf882a3d506fe95b8361f3693ff
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053409"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>El URI que se desea codificar contiene un carácter no válido
Ha intentado codificar una cadena como un URI (Uniform Resource Identifier), pero contenía caracteres no válidos. Aunque la mayoría de los caracteres es válida dentro de las cadenas se conviertan en identificadores URI, algunas secuencias de caracteres Unicode no son válidas.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de que la cadena que se desea codificar contiene solo las secuencias de Unicode válidas. Un URI completo se compone de una secuencia de componentes y los separadores. Los nombres de los corchetes angulares representan los componentes y el ":", "/", ";" y "?" son caracteres reservados que se usan como separadores. El formato general es:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Vea también  
 [encodeURI (función)](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent (Función)](../../javascript/reference/encodeuricomponent-function-javascript.md)