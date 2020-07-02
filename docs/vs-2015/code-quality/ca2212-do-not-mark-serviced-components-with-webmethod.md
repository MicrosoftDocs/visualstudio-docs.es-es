---
title: 'CA2212: no marcar los componentes con servicio con WebMethod | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a3c707fef5562b932b6232300131f6e6e6efef6a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534568"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: No marcar los componentes con servicio como WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|Identificador de comprobación|CA2212|
|Categoría|Microsoft. Usage|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un método de un tipo que hereda de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> se marca con <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName> .

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.Web.Services.WebMethodAttribute>se aplica a los métodos de un servicio Web XML que se crearon con ASP.NET; hace que el método se pueda llamar desde clientes Web remotos. El método y la clase deben ser públicos y ejecutarse en una aplicación Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent>los tipos se hospedan en las aplicaciones COM+ y pueden usar los servicios COM+. <xref:System.Web.Services.WebMethodAttribute>no se aplica a <xref:System.EnterpriseServices.ServicedComponent> los tipos porque no están diseñados para los mismos escenarios. Concretamente, agregar el atributo al <xref:System.EnterpriseServices.ServicedComponent> método no hace que el método se pueda llamar desde clientes Web remotos. Dado que <xref:System.Web.Services.WebMethodAttribute> y un <xref:System.EnterpriseServices.ServicedComponent> método tienen comportamientos y requisitos conflictivos para el flujo de contexto y de transacción, el comportamiento del método será incorrecto en algunos escenarios.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el atributo del <xref:System.EnterpriseServices.ServicedComponent> método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. No hay escenarios en los que la combinación de estos elementos sea correcta.

## <a name="see-also"></a>Consulte también
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
