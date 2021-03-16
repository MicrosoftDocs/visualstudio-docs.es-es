---
description: Se intentó usar instanceof para determinar si un objeto se derivó de una clase de función determinada, pero se ha redefinido la propiedad prototype del objeto como null o como un tipo de objeto externo (ambos objetos JavaScript no válidos).
title: La función no tiene un objeto prototipo válido | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 0356ac9ef7c63c77c0cc0dfca623ff24d3de24af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571420"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>La función no tiene un objeto prototipo válido
Se intentó utilizar **instanceof** para determinar si un objeto se derivó de una clase de función determinada, pero se ha redefinido la `prototype` propiedad del objeto como `null` o como un tipo de objeto externo (ambos objetos no válidos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ). Un objeto externo puede ser un objeto del modelo de objetos host (por ejemplo, un documento o un objeto de ventana de Internet Explorer) o un objeto COM externo.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de que la propiedad de la función `prototype` hace referencia a un [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objeto válido.  
  
## <a name="see-also"></a>Consulte también  
 [Objeto de función](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [prototype (Propiedad, Object)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)
