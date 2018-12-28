---
title: Se esperaba ' @' | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 191402a9ba265e5acfb15d1931e260f6b366687e
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804557"
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