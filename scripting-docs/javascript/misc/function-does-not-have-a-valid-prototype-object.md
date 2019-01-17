---
title: Función no tiene un objeto prototipo válido | Documentos de Microsoft
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
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4e2cbf198a452cd61f1355682ea3041436d2a27
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346701"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>La función no tiene un objeto prototipo válido
Se intentó utilizar **instanceof** para determinar si un objeto se derivó de una clase de función determinada, pero se ha redefinido del objeto `prototype` propiedad como `null`, o un tipo de objeto externo (ambos denoesválido[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos). Un objeto externo puede ser un objeto desde el modelo de objetos de host (por ejemplo, el documento de Internet Explorer o el objeto de ventana) o un objeto COM externo.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Asegúrese de la función `prototype` propiedad hace referencia a una [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objeto.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de función](../../javascript/reference/function-object-javascript.md)   
 [prototype (Propiedad, Object)](../../javascript/reference/prototype-property-object-javascript.md)