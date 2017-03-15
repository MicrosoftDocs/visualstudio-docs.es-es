---
title: "CA2147: Los m&#233;todos transparentes no pueden usar aserciones de seguridad | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SecurityTransparentCodeShouldNotAssert"
  - "CA2147"
  - "CA2128"
helpviewer_keywords: 
  - "CA2128"
  - "SecurityTransparentCodeShouldNotAssert"
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA2147: Los m&#233;todos transparentes no pueden usar aserciones de seguridad
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecurityTransparentCodeShouldNotAssert|  
|Identificador de comprobación|CA2147|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 El código marcado como <xref:System.Security.SecurityTransparentAttribute> no tiene concedidos permisos suficientes para ser asertivo.  
  
## Descripción de la regla  
 Esta regla analiza todos los métodos y tipos de un ensamblado que es 100% transparente o tiene una mezcla de transparente y crítico, y marca cualquier uso declarativo o imperativo de <xref:System.Security.CodeAccessPermission.Assert%2A>.  
  
 En tiempo de ejecución, cualquier llamada a <xref:System.Security.CodeAccessPermission.Assert%2A> desde código transparente hará que se inicie una <xref:System.InvalidOperationException>.  Esto puede producirse tanto en los ensamblados 100% transparentes como en los ensamblados con mezcla de transparente y crítico donde un método o tipo se declara transparente pero incluye una aserción declarativa o imperativa.  
  
 En [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 se incluyó una característica denominada *transparencia*.  Los métodos, campos, interfaces, clases y tipos individuales pueden ser transparentes o críticos.  
  
 El código transparente no puede elevar los privilegios de seguridad.  Por consiguiente, cualquier permiso concedido o demandado pasa automáticamente a través del código al dominio de aplicación del llamador o del host.  Entre los ejemplos de elevaciones se incluyen Asserts, LinkDemands, SuppressUnmanagedCode y código `unsafe`.  
  
## Cómo corregir infracciones  
 Para resolver el problema, marque el código que llama a la aserción con <xref:System.Security.SecurityCriticalAttribute>, o quite la aserción.  
  
## Cuándo suprimir advertencias  
 No suprima los mensajes de esta regla.  
  
## Ejemplo  
 Este código generará errores si `SecurityTestClass` es transparente cuando el método `Assert` inicia una <xref:System.InvalidOperationException>.  
  
 [!code-cs[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]  
  
## Ejemplo  
 Una opción es revisar el código del método SecurityTransparentMethod en el ejemplo siguiente y, si el método se considera seguro para su elevación, marcar SecurityTransparentMethod con crítico para la seguridad. Esto requiere que se realice una auditoría de seguridad detallada y completa sin errores en el método junto con cualquier llamada que se produzca dentro del método bajo la Aserción:  
  
 [!code-cs[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]  
  
 Otra opción es quitar la aserción del código y permitir que todas las peticiones de permiso de E\/S del archivo subsiguientes fluyan más allá de SecurityTransparentMethod hasta el llamador.  Esto habilita las comprobaciones de seguridad.  En este caso, generalmente no se necesita ninguna auditoría de seguridad porque las peticiones de permiso fluirán hasta el llamador y\/o el dominio de aplicación.  Las peticiones de permiso se controlan exhaustivamente mediante la concesión de permisos de directivas de seguridad, entornos de hospedaje y código fuente.  
  
## Vea también  
 [Advertencias de seguridad](../code-quality/security-warnings.md)