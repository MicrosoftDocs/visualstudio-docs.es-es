---
title: "CA2211: Los campos no constantes no deben ser visibles | Microsoft Docs"
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
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
helpviewer_keywords: 
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2211: Los campos no constantes no deben ser visibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NonConstantFieldsShouldNotBeVisible|  
|Identificador de comprobación|CA2211|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un campo estático público o protegido no es constante ni es de sólo lectura.  
  
## Descripción de la regla  
 Los campos estáticos que no son constantes ni de sólo lectura no son seguros para subprocesos.  Obtener acceso a este tipo de campo se debe controlar cuidadosamente y requiere técnicas de programación avanzadas para sincronizar el acceso al objeto de clase.  Puesto que hay aspectos difíciles de aprender, y comprobar un objeto tiene sus propias dificultades, es mejor utilizar los campos estáticos para los datos de almacén que no cambian.  Esta regla se aplica a las bibliotecas; las aplicaciones no deben exponer ningún campo.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, marque la constante de campo como estática o de sólo lectura.  Si no es posible, vuelva a diseñar el tipo utilizando un mecanismo alternativo como una propiedad segura para subprocesos que administra el acceso seguro al campo subyacente.  Tenga en cuenta que los problemas como disputa la contención de bloqueo y los interbloqueos podrían afectar al rendimiento y al comportamiento de la biblioteca.  
  
## Cuándo suprimir advertencias  
 Resulta seguro suprimir una advertencia de esta regla si está desarrollando una aplicación y, por tanto, tiene control total sobre el acceso al tipo que contiene el campo estático.  Los diseñadores de bibliotecas no deben suprimir ninguna advertencia de esta regla; si se utilizan campos estáticos no constantes puede hacer que los desarrolladores no utilicen la biblioteca correctamente.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe esta regla.  
  
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-cs[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]