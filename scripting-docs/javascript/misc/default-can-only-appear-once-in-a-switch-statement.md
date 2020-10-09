---
title: "' default ' solo puede aparecer una vez en una instrucción ' switch ' | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b49b5cfe7076a4a9504500a63f4d47d2f54bcc1a
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862787"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' solo puede aparecer una vez en una instrucción 'switch'.
Ha intentado usar la instrucción **predeterminada** más de una vez dentro de una instrucción switch. El caso predeterminado es siempre la última instrucción Case en una instrucción switch (es el caso de paso a través).  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Quite las instrucciones Case **predeterminadas** adicionales de la `switch` instrucción (use como máximo una instrucción Case predeterminada en la instrucción switch).  
  
## <a name="see-also"></a>Vea también  
 [Switch (instrucción)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/switch)   
 [Controlar el flujo del programa](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Palabras reservadas de JavaScript](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Lexical_grammar)