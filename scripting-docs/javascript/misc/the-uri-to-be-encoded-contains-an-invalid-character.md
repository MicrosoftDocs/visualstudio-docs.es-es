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
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349795"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>El URI que se desea codificar contiene un carácter no válido
Ha intentado codificar una cadena como un URI (Uniform Resource Identifier), pero contenía caracteres no válidos. Aunque la mayoría de los caracteres es válida dentro de las cadenas se conviertan en identificadores URI, algunas secuencias de caracteres Unicode no son válidas.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Asegúrese de que la cadena que se desea codificar contiene solo las secuencias de Unicode válidas. Un URI completo se compone de una secuencia de componentes y los separadores. Los nombres de los corchetes angulares representan los componentes y el ":", "/", ";" y "?" son caracteres reservados que se usan como separadores. El formato general es:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Vea también  
 [encodeURI (función)](../../javascript/reference/encodeuri-function-javascript.md)   
 [encodeURIComponent (Función)](../../javascript/reference/encodeuricomponent-function-javascript.md)