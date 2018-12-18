---
title: '&lt;resumen&gt; (JavaScript) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8ee08ed1e2a5feb1f5a87f7d6337a4b5f1e47a22
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252413"
---
# <a name="ltsummarygt-javascript"></a>&lt;resumen&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica la descripción de una función o un método.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<summary locid="descriptionID">description  
</summary>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `locid`  
 Opcional. Identificador de la información de localización sobre la función o el método. El identificador es un identificador de miembro o corresponde al valor del atributo `name` en un paquete de mensajes definido por los metadatos de OpenAjax. El tipo de identificador depende del formato especificado en el [ \<loc >](../ide/loc-javascript.md) elemento.  
  
 `description`  
 Opcional. Descripción de la función o el método.  
  
## <a name="remarks"></a>Comentarios  
 Los elementos utilizados para anotar funciones, que incluyen [ \<resumen >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), y [ \<devuelve >](../ide/returns-javascript.md), se deben colocar en el cuerpo de la función antes de cualquier instrucción.  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente se muestra cómo usar el elemento `<summary>`.  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Comentarios de documentación XML](../ide/xml-documentation-comments-javascript.md)



