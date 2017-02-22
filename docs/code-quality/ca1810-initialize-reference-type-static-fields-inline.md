---
title: "CA1810: Inicializar campos est&#225;ticos de tipo de referencia insertados | Microsoft Docs"
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
  - "InitializeReferenceTypeStaticFieldsInline"
  - "CA1810"
helpviewer_keywords: 
  - "InitializeReferenceTypeStaticFieldsInline"
  - "CA1810"
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1810: Inicializar campos est&#225;ticos de tipo de referencia insertados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InitializeReferenceTypeStaticFieldsInline|  
|Identificador de comprobación|CA1810|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo de referencia declara un constructor estático explícito.  
  
## Descripción de la regla  
 Cuando un tipo declara un constructor estático explícito, el compilador Just\-In\-Time \(JIT\) agrega una comprobación a cada constructor de instancia y a cada método estático del tipo para asegurarse de que se ha llamado anteriormente al constructor estático.  Se desencadena la inicialización estática cuando se tiene acceso a cualquier miembro estático o cuando se crea una instancia del tipo.  Sin embargo, no se desencadena la inicialización estática si declara una variable del tipo pero no se utiliza, lo que puede ser importante si la inicialización modifica el estado global.  
  
 Cuando se inicializan los datos estáticos en línea y no se declara un constructor estático explícito, los compiladores del lenguaje intermedio de Microsoft \(MSIL\) agregan un marcador `beforefieldinit` y un constructor estático implícito a la definición de tipo de MSIL.  Cuando el compilador JIT encuentra la marca `beforefieldinit`, la mayoría de las veces no se agregan las comprobaciones de constructor estático.  Es seguro que se producirá una inicialización estática en algún momento antes de que se obtenga acceso a cualquiera de los campos estáticos, pero no antes de la invocación de un método estático o un constructor de instancia.  Observe que la inicialización estática puede producirse en cualquier momento después de declarar una variable del tipo.  
  
 Las comprobaciones del constructor estático pueden reducir el rendimiento.  Con frecuencia un constructor estático se utiliza solo para inicializar campos estáticos, en cuyo caso debe asegurarse de que la inicialización estática se produce antes del primer acceso a un campo estático.  El comportamiento `beforefieldinit` es adecuado para éstos y para la mayoría de los otros tipos.  No es adecuado sólo cuando la inicialización estática afecta al estado global y una de las siguientes condiciones es verdadera:  
  
-   El efecto sobre el estado global es costoso y no es necesario si no se utiliza el tipo.  
  
-   Se puede tener acceso a los efectos sobre el estado global sin tener acceso a cualquier campo estático del tipo.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, inicialice todos los datos estáticos cuando se declara y quite el constructor estático.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si el rendimiento no es un aspecto importante; o si los cambios del estado global causados por la inicialización estática son costosos o si debe asegurarse de que se produzcan antes de llamar a un método estático del tipo o de crear una instancia del tipo.  
  
## Ejemplo  
 El siguiente ejemplo muestra un tipo `StaticConstructor` que infringe la regla, y un tipo `NoStaticConstructor`, que reemplaza el constructor estático por una inicialización en línea para cumplir la regla.  
  
 [!code-cs[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]  
  
 Tenga en cuenta la suma del marcador `beforefieldinit` en la definición de MSIL para la clase `NoStaticConstructor`.  
  
  **.class public auto ansi StaticConstructor**  
 **extiende \[mscorlib\]System.Object**  
**{**  
**} \/\/ fin de la clase StaticConstructor**  
**.class public auto ansi beforefieldinit NoStaticConstructor**  
 **extiende \[mscorlib\]System.Object**  
**{**  
**} \/\/ fin de la clase NoStaticConstructor**   
## Reglas relacionadas  
 [CA2207: Inicializar campos estáticos de tipo de valor insertados](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)