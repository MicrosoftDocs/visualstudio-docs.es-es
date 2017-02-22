---
title: "CA2002: No bloquear objetos con identidad d&#233;bil | Microsoft Docs"
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
  - "DoNotLockOnObjectsWithWeakIdentity"
  - "CA2002"
helpviewer_keywords: 
  - "CA2002"
  - "DoNotLockOnObjectsWithWeakIdentity"
ms.assetid: 16100b39-c6fc-452b-8fca-8b459a26c286
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2002: No bloquear objetos con identidad d&#233;bil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotLockOnObjectsWithWeakIdentity|  
|Identificador de comprobación|CA2002|  
|Categoría|Microsoft.Reliability|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un subproceso intenta obtener un bloqueo en un objeto que tiene una identidad débil.  
  
## Descripción de la regla  
 Se dice que un objeto tiene una identidad débil cuando se puede tener acceso directamente a través de los límites del dominio de aplicación.  Un subproceso que intenta obtener un bloqueo en un objeto que tiene identidad débil se puede bloquear con un segundo subproceso en un dominio de aplicación diferente que tenga bloqueado el mismo objeto.  Los siguientes tipos tienen una identidad débil y se marcan mediante la regla:  
  
-   <xref:System.MarshalByRefObject>  
  
-   <xref:System.ExecutionEngineException>  
  
-   <xref:System.OutOfMemoryException>  
  
-   <xref:System.StackOverflowException>  
  
-   <xref:System.String>  
  
-   <xref:System.Reflection.MemberInfo>  
  
-   <xref:System.Reflection.ParameterInfo>  
  
-   <xref:System.Threading.Thread>  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, utilice un objeto de un tipo que no está en la lista en la sección Descripción.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Reglas relacionadas  
 [CA2213: Aplique Dispose a los campos a los que se pueda](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
## Ejemplo  
 El siguiente ejemplo muestra algunos bloqueos de objeto que infringen la regla.  
  
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
 [!code-cs[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]  
  
## Vea también  
 <xref:System.Threading.Monitor>   
 <xref:System.AppDomain>   
 [lock \(Instrucción\)](/dotnet/csharp/language-reference/keywords/lock-statement)   
 [SyncLock \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/synclock-statement)