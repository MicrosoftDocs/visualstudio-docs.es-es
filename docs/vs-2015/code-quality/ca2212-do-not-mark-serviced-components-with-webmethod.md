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
ms.openlocfilehash: 2ee166f8bbc14e66968cd4f7c265331854905ac9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662946"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: No marcar los componentes con servicio como WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|Identificador de comprobación|CA2212|
|Categoría|Microsoft. Usage|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método de un tipo que hereda de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> se marca con <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.Web.Services.WebMethodAttribute> se aplica a los métodos de un servicio Web XML que se crearon con ASP.NET; hace que el método se pueda llamar desde clientes Web remotos. El método y la clase deben ser públicos y ejecutarse en una aplicación Web ASP.NET. las aplicaciones COM+ hospedan los tipos <xref:System.EnterpriseServices.ServicedComponent> y pueden usar los servicios COM+. <xref:System.Web.Services.WebMethodAttribute> no se aplica a los tipos <xref:System.EnterpriseServices.ServicedComponent> porque no están diseñados para los mismos escenarios. En concreto, agregar el atributo al método <xref:System.EnterpriseServices.ServicedComponent> no hace que el método se pueda llamar desde clientes Web remotos. Dado que <xref:System.Web.Services.WebMethodAttribute> y un método <xref:System.EnterpriseServices.ServicedComponent> tienen comportamientos y requisitos conflictivos para el flujo de transacciones y de contexto, el comportamiento del método será incorrecto en algunos escenarios.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el atributo del método <xref:System.EnterpriseServices.ServicedComponent>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. No hay escenarios en los que la combinación de estos elementos sea correcta.

## <a name="see-also"></a>Vea también
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
