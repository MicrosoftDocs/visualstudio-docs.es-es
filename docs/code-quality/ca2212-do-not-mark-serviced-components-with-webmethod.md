---
title: 'CA2212: No marcar los componentes con servicio como WebMethod'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7d1595c6bdf7eafb5b86daba99e943aad3f02ac7
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550653"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: No marcar los componentes con servicio como WebMethod

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|Identificador de comprobación|CA2212|
|Categoría|Microsoft.Usage|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Un método en un tipo que hereda de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> está marcado con <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla

<xref:System.Web.Services.WebMethodAttribute> se aplica a los métodos dentro de un servicio web XML creados utilizando ASP.NET; lo hace el método que se puede llamar desde clientes web remotos. El método y la clase deben ser pública y en ejecución en una aplicación web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> los tipos se hospedan en aplicaciones COM + y pueden usar los servicios COM +. <xref:System.Web.Services.WebMethodAttribute> no se aplica a <xref:System.EnterpriseServices.ServicedComponent> tipos ya que no están destinados a los mismos escenarios. En concreto, cuando se agrega el atributo a la <xref:System.EnterpriseServices.ServicedComponent> método no realiza el método que se puede llamar desde clientes web remotos. Dado que <xref:System.Web.Services.WebMethodAttribute> y un <xref:System.EnterpriseServices.ServicedComponent> método tienen comportamientos en conflicto y requisitos para el contexto y el flujo de transacciones, el comportamiento del método será incorrectos en algunos escenarios.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, quite el atributo de la <xref:System.EnterpriseServices.ServicedComponent> método.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla. No hay ningún escenario donde la combinación de estos elementos es correcta.

## <a name="see-also"></a>Vea también

- <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>
- <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>