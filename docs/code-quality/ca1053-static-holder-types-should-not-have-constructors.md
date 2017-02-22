---
title: "CA1053: Los tipos titulares est&#225;ticos no deben tener constructores | Microsoft Docs"
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
  - "StaticHolderTypesShouldNotHaveConstructors"
  - "CA1053"
helpviewer_keywords: 
  - "CA1053"
  - "StaticHolderTypesShouldNotHaveConstructors"
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1053: Los tipos titulares est&#225;ticos no deben tener constructores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StaticHolderTypesShouldNotHaveConstructors|  
|Identificador de comprobación|CA1053|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo público o público anidado declara sólo miembros estáticos y tiene un constructor predeterminado público o protegido.  
  
## Descripción de la regla  
 El constructor no es necesario puesto que al llamar a los miembros estáticos no se requiere una instancia del tipo.  Además, como el tipo tiene miembros no estáticos, al crear una instancia, no se proporciona acceso a cualquiera de los miembros del tipo.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el constructor predeterminado o márquelo como privado.  
  
> [!NOTE]
>  Algunos compiladores crean automáticamente un constructor predeterminado público si el tipo no define ningún constructor.  Si éste es el caso de su tipo, agregue un constructor predeterminado privado para eliminar la infracción.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  La presencia del constructor sugiere que el tipo no sea un tipo estático.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo que infringe esta regla.  Observe que no hay ningún constructor predeterminado en el código fuente.  Cuando este código se compila en un ensamblado, el compilador de C\# insertará un constructor predeterminado, que infringirá esta regla.  Para corregir esto, declare un constructor privado.  
  
 [!code-cs[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]