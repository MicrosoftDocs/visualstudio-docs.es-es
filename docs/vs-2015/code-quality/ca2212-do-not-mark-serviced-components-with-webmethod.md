---
title: 'CA2212: No marcar los componentes con servicio como WebMethod | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6f2e89705e36407e39103296e3eee70482e3d03f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142485"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: No marcar los componentes con servicio como WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|Identificador de comprobación|CA2212|
|Categoría|Microsoft.Usage|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un método en un tipo que hereda de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> está marcado con <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.Web.Services.WebMethodAttribute> se aplica a los métodos dentro de un servicio Web XML creados utilizando ASP.NET; Esto hace que el método que se puede llamar desde clientes Web remotos. El método y la clase deben ser pública y en ejecución en una aplicación Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> los tipos se hospedan en aplicaciones COM + y pueden usar los servicios COM +. <xref:System.Web.Services.WebMethodAttribute> no se aplica a <xref:System.EnterpriseServices.ServicedComponent> tipos ya que no están destinados a los mismos escenarios. En concreto, cuando se agrega el atributo a la <xref:System.EnterpriseServices.ServicedComponent> método no realiza el método que se puede llamar desde clientes Web remotos. Dado que <xref:System.Web.Services.WebMethodAttribute> y un <xref:System.EnterpriseServices.ServicedComponent> método tienen comportamientos en conflicto y requisitos para el contexto y el flujo de transacciones, el comportamiento del método será incorrectos en algunos escenarios.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el atributo de la <xref:System.EnterpriseServices.ServicedComponent> método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. No hay ningún escenario donde la combinación de estos elementos es correcta.

## <a name="see-also"></a>Vea también
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
