---
title: Se esperaba ') ' en la expresión regular (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: af32127476c83100c0340021428e3abc572ef2f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815648"
---
# <a name="expected--in-regular-expression-javascript"></a>Se esperaba ')' en la expresión regular (JavaScript)
Se intentó crear una captura de expresión regular, una aserción o un grupo, pero no se incluía el paréntesis de cierre. Los paréntesis tienen varios propósitos en expresiones regulares. Principalmente, se usan para capturar subexpresiones, para especificar aserciones o para agrupar patrones de forma que los elementos se puedan tratar como una sola unidad en *, +,?, etc.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Agregue los paréntesis de cierre situados más a la derecha.  
  
    > [!NOTE]
    > Si desea buscar coincidencias con un solo paréntesis, haga una marca de escape con una barra diagonal inversa \\ (-para que no se interprete como carácter especial) [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Vea también  
 [Objeto de expresión regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresiones regulares (JavaScript)](https://msdn.microsoft.com/library/1400241x)