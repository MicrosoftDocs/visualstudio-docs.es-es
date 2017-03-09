---
title: "CA2213: Aplique Dispose a los campos a los que se pueda | Microsoft Docs"
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
  - "DisposableFieldsShouldBeDisposed"
  - "CA2213"
helpviewer_keywords: 
  - "CA2213"
  - "DisposableFieldsShouldBeDisposed"
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2213: Aplique Dispose a los campos a los que se pueda
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposableFieldsShouldBeDisposed|  
|Identificador de comprobación|CA2213|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un tipo que implementa <xref:System.IDisposable?displayProperty=fullName> declara campos que son de tipos que también implementan <xref:System.IDisposable>.  El método <xref:System.IDisposable.Dispose%2A> del tipo declarado no llama al método <xref:System.IDisposable.Dispose%2A> del campo.  
  
## Descripción de la regla  
 Un tipo es responsable de eliminar todos sus recursos no administrados; esto se realiza implementando <xref:System.IDisposable>.  Esta regla comprueba que un tipo `T` disponible declara un campo `F` que sea una instancia de un tipo `FT` disponible.  Para cada campo `F`, la regla intenta buscar una llamada a `FT.Dispose`.  La regla busca los métodos llamados por `T.Dispose` y en uno nivel más bajo \(los métodos llamados por `FT.Dispose`\).  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, llame a <xref:System.IDisposable.Dispose%2A> de los campos que son tipos que implementan <xref:System.IDisposable> si es responsable de asignar y liberar los recursos no administrados contenidos en el campo.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si no es responsable de liberar el recurso contenido en el campo o si la llamada a <xref:System.IDisposable.Dispose%2A> se produce en un nivel de llamada más profundo que el de las comprobaciones de la regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra un tipo `TypeA` que implementa <xref:System.IDisposable> \(`FT` en la explicación anterior\).  
  
 [!code-cs[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]  
  
## Ejemplo  
 El ejemplo siguiente muestra un tipo `TypeB` que infringe esta regla declarando un campo `aFieldOfADisposableType` \(`F` en la explicación anterior\) como un tipo descartable \(`TypeA`\) y no llamando a <xref:System.IDisposable.Dispose%2A> en el campo.  `TypeB` corresponde a `T` en la discusión anterior.  
  
 [!code-cs[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]  
  
## Vea también  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Patrón de Dispose](../Topic/Dispose%20Pattern.md)