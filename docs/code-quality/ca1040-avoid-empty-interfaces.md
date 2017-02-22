---
title: "CA1040: Evitar interfaces vac&#237;as | Microsoft Docs"
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
  - "CA1040"
  - "AvoidEmptyInterfaces"
helpviewer_keywords: 
  - "AvoidEmptyInterfaces"
  - "CA1040"
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1040: Evitar interfaces vac&#237;as
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidEmptyInterfaces|  
|Identificador de comprobación|CA1040|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 La interfaz no declara ningún miembro ni implementa otras dos o más interfaces.  
  
## Descripción de la regla  
 Las interfaces definen miembros que proporcionan un comportamiento o acuerdo de uso.  Cualquier tipo puede adoptar la funcionalidad descrita por la interfaz sin tener en cuenta dónde aparece el tipo en la jerarquía de herencia.  Un tipo implementa una interfaz proporcionando las implementaciones para los miembros de la interfaz.  Una interfaz vacía no define ningún miembro.  Por tanto, no define ningún contrato que pueda implementarse.  
  
 Si su diseño incluye interfaces vacías que esperan implementar los tipos, probablemente esté utilizando una interfaz como marcador o un método para identificar un grupo de tipos.  Si esta identificación se produce en tiempo de ejecución, la forma correcta de lograr esto es utilizar un atributo personalizado.  Utilice la presencia o ausencia del atributo, o las propiedades del atributo, para identificar los tipos de destino.  Si la identificación debe producirse en tiempo de compilación, entonces es aceptable utilizar una interfaz vacía.  
  
## Cómo corregir infracciones  
 Quite la interfaz o agréguele los miembros.  Si la interfaz vacía se utiliza para etiquetar un conjunto de tipos, reemplace la interfaz con un atributo personalizado.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si se utiliza la interfaz para identificar un conjunto de tipos en tiempo de compilación.  
  
## Ejemplo  
 El ejemplo siguiente muestra una interfaz vacía.  
  
 [!code-cs[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CSharp/ca1040-avoid-empty-interfaces_1.cs)]
 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/CPP/ca1040-avoid-empty-interfaces_1.cpp)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../code-quality/codesnippet/VisualBasic/ca1040-avoid-empty-interfaces_1.vb)]