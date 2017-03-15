---
title: "CA2114: La seguridad del m&#233;todo deber&#237;a ser un supraconjunto del tipo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MethodSecurityShouldBeASupersetOfType"
  - "CA2114"
helpviewer_keywords: 
  - "CA2114"
  - "MethodSecurityShouldBeASupersetOfType"
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2114: La seguridad del m&#233;todo deber&#237;a ser un supraconjunto del tipo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MethodSecurityShouldBeASupersetOfType|  
|Identificador de comprobación|CA2114|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo tiene seguridad declarativa y uno de sus métodos dispone de seguridad declarativa para la misma acción de seguridad, y ésta no es [Link Demands](../Topic/Link%20Demands.md) ni [Inheritance Demands](http://msdn.microsoft.com/es-es/28b9adbb-8f08-4f10-b856-dbf59eb932d9) y, además, los permisos comprobados por el tipo no son un subconjunto de permisos comprobados por el método.  
  
## Descripción de la regla  
 Un método no debe tener un nivel de método ni un nivel de tipo seguridad declarativa para la misma acción.  No se combinan las dos comprobaciones; sólo se aplica la solicitud de nivel de método.  Por ejemplo, si un tipo solicita un permiso `X` y uno de sus métodos solicita un permiso `Y`, el código no necesita el permiso `X` para ejecutar el método.  
  
## Cómo corregir infracciones  
 Revise su código para asegurase de que ambas acciones son necesarias.  Si son necesarias, asegúrese de que la acción de nivel de método incluye la seguridad especificada en el nivel de tipo.  Por ejemplo, si el tipo solicita el permiso `X` y su método también debe solicitar el permiso `Y`, el método debe solicitar explícitamente `X` y `Y`.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si el método no necesita la seguridad especificada por el tipo.  Sin embargo, no se trata de un escenario común y podría indicar que es necesario revisar cuidadosamente el diseño.  
  
## Ejemplo  
 El ejemplo siguiente utiliza los permisos del entorno para mostrar los riesgos de infringir esta regla.  En este ejemplo, el código de aplicación crea una instancia del tipo asegurado antes de denegar el permiso necesario por el tipo.  En una situación de riesgo real, la aplicación necesitaría otra manera de obtener una instancia del objeto.  
  
 En el ejemplo siguiente, la biblioteca solicita permiso de escritura para un tipo y permiso de lectura para un método.  
  
 [!code-cs[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]  
  
## Ejemplo  
 El código de aplicación siguiente muestra la vulnerabilidad de la biblioteca llamando al método aunque no cumple el nivel de tipo requisito de seguridad de nivel de tipo.  
  
 [!code-cs[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **\[Todos los permisos\] datos personales: 16\/6\/1964 12:00:00 a.m.**  
**\[Sin permiso de escritura \(exigido por el tipo\)\] datos personales: 16\/6\/1964 12:00:00 a.m.**  
**\[Sin permiso de lectura \(exigido por el método\)\] no se pudo tener acceso a los datos personales: se produjo un error en la solicitud.**   
## Vea también  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Inheritance Demands](http://msdn.microsoft.com/es-es/28b9adbb-8f08-4f10-b856-dbf59eb932d9)   
 [Link Demands](../Topic/Link%20Demands.md)   
 [Datos y modelado](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)