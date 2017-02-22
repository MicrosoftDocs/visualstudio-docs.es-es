---
title: "CA1721: Los nombres de propiedades no deber&#237;an coincidir con los m&#233;todos Get | Microsoft Docs"
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
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
helpviewer_keywords: 
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1721: Los nombres de propiedades no deber&#237;an coincidir con los m&#233;todos Get
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertyNamesShouldNotMatchGetMethods|  
|Identificador de comprobación|CA1721|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## Motivo  
 El nombre de un miembro público o protegido comienza con "Get" y en cualquier otro caso coincide con el nombre de una propiedad pública o protegida.  Por ejemplo, un tipo que contiene un método denominado "GetColor" y una propiedad denominada "Color" infringe esta regla.  
  
## Descripción de la regla  
 Las propiedades y métodos Get deberían tener nombres que distingan claramente su función.  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime.  Esto reduce el tiempo de aprendizaje necesario para la nueva biblioteca de software y aumenta la confianza por parte del cliente en lo que respecta a que la biblioteca fue desarrollada por un especialista en desarrollo de código administrado.  
  
## Cómo corregir infracciones  
 Cambie el nombre para que no coincida con el nombre de un método con el prefijo "Get".  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
> [!NOTE]
>  Se puede excluir esta advertencia si el método Get se produce por la implementación de la interfaz IExtenderProvider.  
  
## Ejemplo  
 El ejemplo siguiente contiene un método y una propiedad que infringen esta regla.  
  
 [!code-cs[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]  
  
## Reglas relacionadas  
 [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)