---
title: '&lt;summary&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f283c2c1825c4b8b02fb5b044ce113231a919317
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646846"
---
# <a name="ltsummarygt-javascript"></a>&lt;summary&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica la descripción de una función o un método.

## <a name="syntax"></a>Sintaxis

```
<summary locid="descriptionID">description
</summary>
```

#### <a name="parameters"></a>Parámetros
 `locid` Opcional. Identificador de la información de localización sobre la función o el método. El identificador es un identificador de miembro o corresponde al valor del atributo `name` en un paquete de mensajes definido por los metadatos de OpenAjax. El tipo de identificador depende del formato especificado en el [\<loc>](../ide/loc-javascript.md) elemento.

 `description` Opcional. Descripción de la función o el método.

## <a name="remarks"></a>Observaciones
 Los elementos utilizados para anotar funciones, entre los [\<summary>](../ide/summary-javascript.md) que [\<param>](../ide/param-javascript.md) se incluyen, y [\<returns>](../ide/returns-javascript.md) , se deben colocar en el cuerpo de la función antes de cualquier instrucción.

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

## <a name="see-also"></a>Consulte también
 [Comentarios de la documentación XML](../ide/xml-documentation-comments-javascript.md)
