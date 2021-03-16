---
description: Ha intentado crear una variable que se va a usar con instrucciones de compilación condicional mediante la @set instrucción, pero no ha colocado un arroba @ antes del nombre de la variable.
title: Se esperaba ' @ ' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: e7aa02ed1e436c92014d44e57f2c71ff7db5f99b
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570627"
---
# <a name="expected-"></a>Se esperaba "\@"
Ha intentado crear una variable que se va a usar con instrucciones de compilación condicional mediante la `@set` instrucción, pero no ha colocado una arroba " **@** " antes del nombre de la variable.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Agregue un arroba " **@** " inmediatamente antes del nombre de la variable. Por ejemplo:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Consulte también  
 [@set Privacidad](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-set)   
 [Compilación condicional](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/121hztk3(v=vs.84))   
 [Variables de compilación condicional](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/s59bkzce(v=vs.84))
