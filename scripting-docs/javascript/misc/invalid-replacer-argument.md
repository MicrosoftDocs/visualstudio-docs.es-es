---
title: Argumento de reemplazo no válido | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 452af60c37e4a56996438cc2957e9b69ccee98ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816831"
---
# <a name="invalid-replacer-argument"></a>Argumento reemplazante no válido
Se ha intentado invocar `JSON.stringify` con un argumento que no es válido. El `replacer` argumento debe ser una función o una matriz.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Cambie el `replacer` argumento a una función o una matriz.  
  
## <a name="example"></a>Ejemplo  
 El código de este ejemplo produce un error en tiempo `memberfilter` de ejecución porque es un objeto en lugar de una función o una matriz.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>Consulte también  
 [Objeto JSON](../../javascript/reference/json-object-javascript.md)   
 [JSON. Parse (función)](../../javascript/reference/json-parse-function-javascript.md)   
 [Errores en tiempo de ejecución de JavaScript](../../javascript/reference/javascript-run-time-errors.md)