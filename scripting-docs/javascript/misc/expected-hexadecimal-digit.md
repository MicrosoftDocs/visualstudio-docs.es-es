---
title: Se esperaba un dígito hexadecimal | Documentos de Microsoft
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
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9e29131c4ecf4f476a30da94ec67676d6bea347
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836182"
---
# <a name="expected-hexadecimal-digit"></a>Se esperaba un dígito hexadecimal
Crea una secuencia de escape Unicode incorrecta. Secuencias de escape Unicode comienzan con \u, seguido de cuatro dígitos hexadecimales (nada más y nada menos). Dígitos hexadecimales Unicode pueden contener los números 0-9, las letras mayúsculas A-f y las letras en minúsculas a f. El ejemplo siguiente muestra una secuencia de escape Unicode tiene el formato correcto.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Asegúrese de que los dígitos hexadecimales Unicode comienzan con \u, contiene los números 0-9, las letras mayúsculas A-F, las minúsculas letras a-f; y se agrupan en cuatro dígitos.  
  
    > [!NOTE]
    >  Si desea utilizar el texto literal \u en una cadena y, después, utilice dos barras diagonales inversas - (\\\u)-escape de la barra diagonal inversa primera.  
  
## <a name="see-also"></a>Vea también  
 [Tipos de datos](../../javascript/data-types-javascript.md)