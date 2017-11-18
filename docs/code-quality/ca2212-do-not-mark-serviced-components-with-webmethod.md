---
title: 'CA2212: No marcar los componentes con WebMethod | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 44c29215301212a12c5652fbf1fe91af23db1082
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: No marcar los componentes con servicio como WebMethod
|||  
|-|-|  
|TypeName|DoNotMarkServicedComponentsWithWebMethod|  
|Identificador de comprobación|CA2212|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un método en un tipo que hereda de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> se marca con <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Descripción de la regla  
 <xref:System.Web.Services.WebMethodAttribute>se aplica a los métodos dentro de un servicio Web XML creados mediante ASP.NET; Esto hace que el método que se puede llamar desde clientes Web remotos. El método y la clase deben ser pública y se ejecutan en una aplicación Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent>tipos se hospedan en aplicaciones COM + y pueden usar los servicios COM +. <xref:System.Web.Services.WebMethodAttribute>no se aplica a <xref:System.EnterpriseServices.ServicedComponent> tipos, ya que no están pensados para los mismos escenarios. En concreto, agregar el atributo a la <xref:System.EnterpriseServices.ServicedComponent> método no haga que el método que se puede llamar desde clientes Web remotos. Dado que <xref:System.Web.Services.WebMethodAttribute> y un <xref:System.EnterpriseServices.ServicedComponent> método tienen comportamientos en conflicto y requisitos de contexto y el flujo de transacciones, el comportamiento del método es incorrectos en algunas situaciones.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el atributo de la <xref:System.EnterpriseServices.ServicedComponent> método.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla. No hay ningún escenario donde la combinación de estos elementos es correcta.  
  
## <a name="see-also"></a>Vea también  
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>   
 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>