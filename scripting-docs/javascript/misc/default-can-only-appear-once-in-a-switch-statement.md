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
ms.openlocfilehash: 0fdce6a86665b942098e4542dc237bc1ef22ad8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815518"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' solo puede aparecer una vez en una instrucción 'switch'.
Ha intentado usar la instrucción **predeterminada** más de una vez dentro de una instrucción switch. El caso predeterminado es siempre la última instrucción Case en una instrucción switch (es el caso de paso a través).  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Quite las instrucciones Case **predeterminadas** adicionales de la `switch` instrucción (use como máximo una instrucción Case predeterminada en la instrucción switch).  
  
## <a name="see-also"></a>Vea también  
 [Switch (instrucción)](../../javascript/reference/switch-statement-javascript.md)   
 [Controlar el flujo del programa](../../javascript/controlling-program-flow-javascript.md)   
 [Palabras reservadas de JavaScript](../../javascript/reference/javascript-reserved-words.md)