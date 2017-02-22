---
title: "CA2214: No llamar a m&#233;todos reemplazables en constructores | Microsoft Docs"
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
  - "DoNotCallOverridableMethodsInConstructors"
  - "CA2214"
helpviewer_keywords: 
  - "CA2214"
  - "DoNotCallOverridableMethodsInConstructors"
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2214: No llamar a m&#233;todos reemplazables en constructores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotCallOverridableMethodsInConstructors|  
|Identificador de comprobación|CA2214|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 El constructor de un tipo no sellado llama a un método virtual definido en su clase.  
  
## Descripción de la regla  
 Cuando se llama a un método virtual, el tipo real que ejecuta el método no se selecciona hasta el tiempo de ejecución.  Cuando un constructor llama a un método virtual, es posible que no se haya ejecutado el constructor para la instancia que invoca el método.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, no llame a los métodos virtuales del tipo desde los constructores del tipo.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  El constructor se debería rediseñar para eliminar la llamada al método virtual.  
  
## Ejemplo  
 El ejemplo siguiente muestra el efecto de la infracción de esta regla.  La aplicación de prueba crea una instancia de `DerivedType`, que hace que se ejecute el constructor de la clase base \(`BadlyConstructedType`\).  El constructor de `BadlyConstructedType` llama incorrectamente al método virtual `DoSomething`.  Tal como muestra el resultado, `DerivedType.DoSomething()` se ejecuta y así lo hace antes de que se ejecute el constructor de `DerivedType`.  
  
 [!code-cs[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **Llamar al constructor base.**  
**Se llama a DoSomething derivado, ¿inicializado?  No**  
**Llamar al constructor derivado.**