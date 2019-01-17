---
title: Se esperaba ')' en la expresión regular (JavaScript) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c344105010e406ef4936fdcca58baffbd610088
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347429"
---
# <a name="expected--in-regular-expression-javascript"></a>Se esperaba ')' en la expresión regular (JavaScript)
Se ha intentado crear una captura de expresión regular, la aserción o el grupo, pero no incluía el paréntesis de cierre. Los paréntesis tienen varios propósitos en expresiones regulares. Principalmente, se utilizan para capturar subexpresiones, para especificar las aserciones, o para agrupar patrones para que los elementos se pueden tratar como una sola unidad por *, +,?, y así sucesivamente.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Agregue el paréntesis de cierre situado.  
  
    > [!NOTE]
    >  Si desea asociar un paréntesis único, un carácter de escape con una barra diagonal inversa - \\(: para que no se interpreta como un carácter especial por [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Objeto de expresión regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](https://msdn.microsoft.com/library/1400241x)