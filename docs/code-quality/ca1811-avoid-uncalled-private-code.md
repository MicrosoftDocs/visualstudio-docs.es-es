---
title: "CA1811: Evitar c&#243;digo privado al que no se llama | Microsoft Docs"
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
  - "AvoidUncalledPrivateCode"
  - "CA1811"
helpviewer_keywords: 
  - "CA1811"
  - "AvoidUncalledPrivateCode"
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1811: Evitar c&#243;digo privado al que no se llama
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUncalledPrivateCode|  
|Identificador de comprobación|CA1811|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un miembro interno o privado \(nivel de ensamblado\) no tiene llamadores en el ensamblado, no es invocado por Common Language Runtime ni tampoco por un delegado.  Esta regla no comprueba los miembros siguientes:  
  
-   Miembros de interfaz explícitos.  
  
-   Constructores estáticos.  
  
-   Constructores de serialización.  
  
-   Los métodos marcados con <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> o <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.  
  
-   Miembros que son reemplazan.  
  
## Descripción de la regla  
 Esta regla puede crear un informe con falsos positivos si hay puntos de entrada que no son identificados actualmente por la lógica de la regla.  Asimismo, un compilador puede emitir código no invocable en un ensamblado.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el código que no sea invocable o agregue código que lo llame.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla.  
  
## Reglas relacionadas  
 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)