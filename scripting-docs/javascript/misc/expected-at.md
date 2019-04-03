---
title: Se esperaba '@' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05842c274c27165a7065cb90fda60dd75da2a659
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840343"
---
# <a name="expected-"></a>Se esperaba '@'
Se intentó crear una variable para su uso con instrucciones de compilación condicional mediante el `@set` instrucción, pero no realizó una arroba "**@**" antes del nombre de variable.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Agregue un signo "**@**" inmediatamente antes del nombre de variable. Por ejemplo:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Vea también  
 [@set instrucción](../../javascript/reference/at-set-statement-javascript.md)   
 [Compilación condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilación condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)