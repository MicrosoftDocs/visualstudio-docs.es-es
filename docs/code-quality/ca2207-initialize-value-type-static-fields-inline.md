---
title: "CA2207: Inicializar campos est&#225;ticos de tipo de valor insertados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InitializeValueTypeStaticFieldsInline"
  - "CA2207"
helpviewer_keywords: 
  - "CA2207"
  - "InitializeValueTypeStaticFieldsInline"
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2207: Inicializar campos est&#225;ticos de tipo de valor insertados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InitializeValueTypeStaticFieldsInline|  
|Identificador de comprobación|CA2207|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un tipo de valor declara un constructor estático explícito.  
  
## Descripción de la regla  
 Al declarar un tipo de valor, se realiza una inicialización predeterminada en la que los campos de tipo de valor se establecen en cero y los campos de tipo de referencia se establecen en `null` \(`Nothing` en Visual Basic\).  Un constructor estático explícito sólo garantiza la ejecución antes de llamar al constructor de la instancia o al miembro estático del tipo.  Por tanto, si se crea el tipo sin haber llamado al constructor de la instancia, el constructor estático no garantiza la ejecución.  
  
 Si los datos estáticos se inicializan en línea y no se declara el constructor estático explícito, los compiladores de C\# y Visual Basic agregan el marcador `beforefieldinit` a la definición de clase de MSIL.  Además, los compiladores agregan un constructor estático privado que contiene código de inicialización estática.  Este constructor estático privado garantiza la ejecución antes de obtener acceso a cualquier campo estático del tipo.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, inicialice todos los datos estáticos cuando se declara y quite el constructor estático.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Reglas relacionadas  
 [CA1810: Inicializar campos estáticos de tipo de referencia insertados](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)