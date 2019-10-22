---
title: La función no tiene un objeto prototipo válido | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb3cffa4bffd616560aa95ace4ad82a4368ebbd5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574599"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>La función no tiene un objeto prototipo válido
Se intentó utilizar **instanceof** para determinar si un objeto se derivó de una clase de función determinada, pero se ha redefinido la propiedad `prototype` del objeto como `null` o como un tipo de objeto externo (ambos objetos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] no válidos). Un objeto externo puede ser un objeto del modelo de objetos host (por ejemplo, un documento o un objeto de ventana de Internet Explorer) o un objeto COM externo.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de que la propiedad `prototype` de la función hace referencia a un objeto [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] válido.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de función](../../javascript/reference/function-object-javascript.md)    
 [prototype (Propiedad, Object)](../../javascript/reference/prototype-property-object-javascript.md)