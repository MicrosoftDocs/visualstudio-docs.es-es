---
title: '&lt;en desuso&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b93a2b4dcc541f32c16766da0dd9dd19a4fdfe0d
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54759761"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;deprecated&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica una función o un método en desuso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<deprecated  
    type="deprecate|remove"  
    locid="descriptionID">description  
</deprecated>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `type`  
 Opcional. Especifica si la función o el método se quitará en futuras versiones, o si la función o el método ya se ha quitado y su uso puede producir un error. Establézcalo en `deprecate` para especificar que la función o el método se quitará en futuras versiones. Establézcalo en `remove` para especificar que la función o el método ya se ha quitado.  
  
 `locid`  
 Opcional. Identificador de la información de localización sobre la función o el método. El identificador es un identificador de miembro o corresponde al valor del atributo `name` en un paquete de mensajes definido por los metadatos de OpenAjax. El tipo de identificador depende del formato especificado en el [ \<loc >](../ide/loc-javascript.md) elemento.  
  
 `description`  
 Opcional. Descripción de la función o el método que se va a estar en desuso.  
  
## <a name="remarks"></a>Comentarios  
 Los elementos utilizados para anotar funciones, entre los que se incluye `<deprecated>`, se deben colocar en el cuerpo de la función antes de cualquier instrucción. Al marcar una función como en desuso, le recomendamos que reemplace su [ \<resumen >](../ide/summary-javascript.md) elemento con el `<deprecated>` elemento.  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente se muestra cómo usar el elemento `<deprecated>`.  
  
```javascript  
function areaFunction(radiusParam) {  
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md)
