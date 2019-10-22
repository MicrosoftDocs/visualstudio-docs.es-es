---
title: Se esperaba ' @ ' | Microsoft Docs
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
ms.openlocfilehash: df1c62c00fdfc8b2b28300cbca1052f0fa350b32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576509"
---
# <a name="expected-"></a>Se esperaba ' \@ '
Ha intentado crear una variable que se va a usar con instrucciones de compilación condicional mediante la instrucción `@set`, pero no ha colocado una arroba " **@** " antes del nombre de la variable.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Agregue un arroba " **@** " inmediatamente antes del nombre de la variable. Por ejemplo:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Vea también  
 [@set instrucción](../../javascript/reference/at-set-statement-javascript.md)    
 @No__t_1 de [compilación condicional](../../javascript/advanced/conditional-compilation-javascript.md)  
 [Variables de compilación condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)
