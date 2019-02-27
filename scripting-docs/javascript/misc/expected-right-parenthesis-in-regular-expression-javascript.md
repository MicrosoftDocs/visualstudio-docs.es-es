---
title: Se esperaba ')' en la expresión regular (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72b4cf24b4b738b7ca71e364d7be6486313a4844
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840810"
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