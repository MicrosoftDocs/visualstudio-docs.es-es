---
title: Función no tiene un objeto prototipo válido | Documentos de Microsoft
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
ms.openlocfilehash: 31226f972ff4714dd81207cf27d862d3449184a5
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840768"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>La función no tiene un objeto prototipo válido
Se intentó utilizar **instanceof** para determinar si un objeto se derivó de una clase de función determinada, pero se ha redefinido del objeto `prototype` propiedad como `null`, o un tipo de objeto externo (ambos denoesválido[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos). Un objeto externo puede ser un objeto desde el modelo de objetos de host (por ejemplo, el documento de Internet Explorer o el objeto de ventana) o un objeto COM externo.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Asegúrese de la función `prototype` propiedad hace referencia a una [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objeto.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de función](../../javascript/reference/function-object-javascript.md)   
 [prototype (Propiedad, Object)](../../javascript/reference/prototype-property-object-javascript.md)