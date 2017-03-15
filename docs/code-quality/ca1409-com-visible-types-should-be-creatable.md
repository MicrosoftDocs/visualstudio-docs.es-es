---
title: "CA1409: Los tipos visibles COM se deben poder crear | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
helpviewer_keywords: 
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1409: Los tipos visibles COM se deben poder crear
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComVisibleTypesShouldBeCreatable|  
|Identificador de comprobación|CA1409|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo de referencia marcado específicamente como visible para el Modelo de objetos componentes \(COM\) contiene un constructor parametrizado público pero no contiene un constructor \(sin parámetros\) predeterminado público.  
  
## Descripción de la regla  
 Un tipo sin un constructor predeterminado público no se puede crear mediante clientes COM.  Sin embargo, los clientes COM aún pueden obtener acceso al tipo si está disponible otro medio para crear el tipo y pasarlo al cliente \(por ejemplo, mediante el valor que se devuelve al llamar a un método\).  
  
 La regla omite los tipos que se derivan de <xref:System.Delegate?displayProperty=fullName>.  
  
 De manera predeterminada, son visibles para COM: ensamblados, tipos públicos, miembros de instancia públicos de tipos públicos y todos los miembros de tipos de valor públicos.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue un constructor predeterminado público o quite <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> del tipo.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si se proporcionan otras formas de crear y pasar el objeto al cliente COM.  
  
## Reglas relacionadas  
 [CA1017: Marcar los ensamblados con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Vea también  
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)