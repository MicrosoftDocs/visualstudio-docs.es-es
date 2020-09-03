---
title: Attribute (Propiedad dinámica de XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 551e072b05e7a88ff9624c5d16e4aa199a6afd66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657981"
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (Propiedad dinámica de XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtiene un indizador que se usa para recuperar la instancia del atributo que se corresponde con el nombre expandido especificado.

## <a name="syntax"></a>Sintaxis

```
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto
 Un indizador del tipo `XAttribute Item(String expandedName)`. Este indizador toma el nombre expandido del atributo especificado y devuelve el elemento <xref:System.Xml.Linq.XAttribute> correspondiente, o bien `null` si no existe ningún atributo con el nombre especificado.

## <a name="remarks"></a>Observaciones
 Esta propiedad es equivalente al método <xref:System.Xml.Linq.XElement.Attribute%2A> de la clase <xref:System.Xml.Linq.XElement?displayProperty=fullName>.

## <a name="see-also"></a>Consulte también
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>[Valor](../designers/value-xattribute-dynamic-property.md) de [las propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)
