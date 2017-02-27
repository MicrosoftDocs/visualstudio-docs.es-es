---
title: "CA1801: Revisar par&#225;metros sin utilizar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidUnusedParameters"
  - "CA1801"
  - "ReviewUnusedParameters"
helpviewer_keywords: 
  - "CA1801"
  - "ReviewUnusedParameters"
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 30
---
# CA1801: Revisar par&#225;metros sin utilizar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewUnusedParameters|  
|Identificador de comprobación|CA1801|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|Poco problemático: si el miembro no se puede ver fuera del ensamblado, independientemente del cambio realizado.<br /><br /> Poco problemático: si cambia el miembro para utilizar el parámetro dentro de su cuerpo.<br /><br /> Problemático: si quita el parámetro y está visible fuera del ensamblado.|  
  
## Motivo  
 Una firma de método incluye un parámetro que no se utiliza en el cuerpo del método.  Esta regla no examina los siguientes métodos:  
  
-   Métodos a los que hace referencia un delegado.  
  
-   Métodos utilizados como controladores de eventos.  
  
-   Los métodos declarados con el modificador `abstract` \(`MustOverride` en Visual Basic\).  
  
-   Los métodos declarados con el modificador `virtual` \(`Overridable` en Visual Basic\).  
  
-   Los métodos declarados con el modificador `override` \(`Overrides` en Visual Basic\).  
  
-   Los métodos declarados con el modificador `extern` \(la instrucción `Declare` en Visual Basic\).  
  
## Descripción de la regla  
 Revise los parámetros de métodos no virtuales que no se utilizan en el cuerpo del método para asegurarse de que no hay exactitud en torno al error para tener acceso a ellos.  Los parámetros no utilizados incurren en mantenimiento y costos de rendimiento.  
  
 A veces una infracción de esta regla puede indicar un error en la implementación del método.  Por ejemplo, el parámetro debería haberse utilizado en el cuerpo del método.  Suprima las advertencias de esta regla si el parámetro tiene que existir por compatibilidad con versiones anteriores.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el parámetro que no se utiliza \(un cambio importante\) o utilice el parámetro en el cuerpo del método \(un cambio poco importante\).  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla para el código previamente distribuido para el que la corrección supondría un cambio importante.  
  
## Ejemplo  
 En el ejemplo siguiente se muestran dos métodos.  Un método infringe la regla y el otro método satisface la regla.  
  
 [!code-cs[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]  
  
## Reglas relacionadas  
 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)