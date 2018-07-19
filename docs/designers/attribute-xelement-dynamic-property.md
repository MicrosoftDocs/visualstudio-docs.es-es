---
title: Attribute (Propiedad dinámica de XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: caacdd787f1765721d281db885364aafc36c5183
ms.sourcegitcommit: 522ba712c0d625e51352506146b0556414681964
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37890014"
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (Propiedad dinámica de XElement)

Obtiene un indizador que se usa para recuperar la instancia del atributo que se corresponde con el nombre expandido especificado.

## <a name="syntax"></a>Sintaxis

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Un indizador del tipo `XAttribute Item(String expandedName)`. Este indizador toma el nombre expandido del atributo especificado y devuelve el elemento <xref:System.Xml.Linq.XAttribute> correspondiente, o bien `null` si no existe ningún atributo con el nombre especificado.

## <a name="remarks"></a>Comentarios

Esta propiedad es equivalente al método <xref:System.Xml.Linq.XElement.Attribute%2A> de la clase <xref:System.Xml.Linq.XElement?displayProperty=fullName>.

## <a name="see-also"></a>Vea también

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)
- [Valor](../designers/value-xattribute-dynamic-property.md)