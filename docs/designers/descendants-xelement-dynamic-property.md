---
title: Descendants (Propiedad dinámica de XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7255753445d014b1ab59f6e2e8143b341b28a892
ms.sourcegitcommit: 522ba712c0d625e51352506146b0556414681964
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37890258"
---
# <a name="descendants-xelement-dynamic-property"></a>Descendants (Propiedad dinámica de XElement)

Obtiene un indizador que se usa para recuperar todos los descendientes del elemento actual que coinciden con el nombre expandido especificado.

## <a name="syntax"></a>Sintaxis

```xaml
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Un indizador del tipo `IEnumerable<XElement> Item(String expandedName)`. Este indizador toma el nombre expandido de los elementos descendientes especificados y devuelve los elementos secundarios coincidentes en una colección <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.

## <a name="remarks"></a>Comentarios

Esta propiedad es equivalente al método <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> de la clase <xref:System.Xml.Linq.XContainer>.

Los elementos de la colección devuelta están en el orden del documento de origen XML.

Esta propiedad usa la ejecución aplazada.

## <a name="see-also"></a>Vea también

- [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)
- [Elements](../designers/elements-xelement-dynamic-property.md)