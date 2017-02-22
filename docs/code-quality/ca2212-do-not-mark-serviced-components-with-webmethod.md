---
title: "CA2212: No marcar los componentes con servicio como WebMethod | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
helpviewer_keywords: 
  - "CA2212"
  - "DoNotMarkServicedComponentsWithWebMethod"
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2212: No marcar los componentes con servicio como WebMethod
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotMarkServicedComponentsWithWebMethod|  
|Identificador de comprobación|CA2212|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método de un tipo que hereda de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> se marca con <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.  
  
## Descripción de la regla  
 <xref:System.Web.Services.WebMethodAttribute> se aplica a los métodos dentro de un servicio Web XML creado mediante ASP.NET; esto hace que el método sea invocable desde los clientes Web remotos.  El método y la clase deben ser públicos, y se ejecutan en una aplicación Web ASP.NET.  Los tipos <xref:System.EnterpriseServices.ServicedComponent> se hospedan en aplicaciones COM\+ y pueden usar los servicios COM\+.  <xref:System.Web.Services.WebMethodAttribute> no se aplica a los tipos <xref:System.EnterpriseServices.ServicedComponent> porque no están pensados para los mismos escenarios.  De forma específica, agregar el atributo al método <xref:System.EnterpriseServices.ServicedComponent> no hace que el método sea invocable desde los clientes Web remotos.  Puesto que un método <xref:System.Web.Services.WebMethodAttribute> y otro <xref:System.EnterpriseServices.ServicedComponent> tienen comportamientos y requisitos conflictivos para el flujo de transacción y el contexto, el comportamiento del método es incorrecto en algunas situaciones.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el atributo del método <xref:System.EnterpriseServices.ServicedComponent>.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  No hay ningún escenario donde sea correcto combinar estos elementos.  
  
## Vea también  
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>   
 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>