---
title: Se esperaba un dígito hexadecimal | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6672046e0f7bf5e39c334dc0ba30f22eaff6e9a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573375"
---
# <a name="expected-hexadecimal-digit"></a>Se esperaba un dígito hexadecimal
Ha creado una secuencia de escape Unicode incorrecta. Las secuencias de escape Unicode comienzan con \u, seguido de exactamente cuatro dígitos hexadecimales (no más y menos). Los dígitos hexadecimales Unicode solo pueden contener los números 0-9, las letras mayúsculas A-F y las minúsculas a-f. En el ejemplo siguiente se muestra una secuencia de escape Unicode formada correctamente.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de que los dígitos hexadecimales de Unicode comienzan por \u, contiene solo los números 0-9, las letras mayúsculas A-F, las minúsculas a-f; y se agrupan en cuatro dígitos.  
  
    > [!NOTE]
    > Si desea usar el texto literal \u en una cadena, utilice dos barras diagonales inversas (\\ \u)-una para escapar la primera barra diagonal inversa.  
  
## <a name="see-also"></a>Vea también  
 [Tipos de datos](../../javascript/data-types-javascript.md)