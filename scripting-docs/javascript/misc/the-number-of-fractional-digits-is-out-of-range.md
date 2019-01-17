---
title: El número de dígitos fraccionarios está fuera del intervalo | Documentos de Microsoft
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
- VS.WebClient.Help.SCRIPT5026
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dbe05d7d-fcf6-4823-9c61-4b814d1ad3c4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17ffec5e6b4cfff85b49f61e7105ca8ce3d75c78
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348469"
---
# <a name="the-number-of-fractional-digits-is-out-of-range"></a>El número de dígitos fraccionarios está fuera de intervalo
Se intentó pasar un argumento no válido a la función **Number.prototype.toExponential**. El argumento a la función **toExponential()** debe estar comprendido entre 0 y 20 (ambos inclusive).  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Garantizar que el argumento para **toExponential()** no es demasiado grande o demasiado pequeño.  
  
## <a name="see-also"></a>Vea también  
 [toExponential (Método, Number)](../../javascript/reference/toexponential-method-number-javascript.md)