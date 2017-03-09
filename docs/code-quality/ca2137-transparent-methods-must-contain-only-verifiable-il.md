---
title: "CA2137: Los m&#233;todos transparentes deben contener solo IL que se pueda comprobar | Microsoft Docs"
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
  - "CA2137"
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2137: Los m&#233;todos transparentes deben contener solo IL que se pueda comprobar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustBeVerifiable|  
|Identificador de comprobación|CA2137|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método contiene código que no se puede comprobar o devuelve un tipo por referencia.  
  
## Descripción de la regla  
 Esta regla se desencadena en los intentos del código transparente en seguridad de ejecutar MSIL no comprobable \(Lenguaje intermedio de Microsoft\).  Sin embargo, la regla no contiene un comprobador de IL completo y, en su lugar, utiliza la heurística para detectar la mayoría de las infracciones de comprobación MSIL.  
  
 Para estar seguro de que su código solo contiene MSIL comprobable, ejecute [Peverify.exe \(PEVerify Tool\)](../Topic/Peverify.exe%20\(PEVerify%20Tool\).md) en su ensamblado.  Ejecute PEVerify con la opción **\/transparent** que limita la salida solo a los métodos transparentes inaveriguables que producirían un error.  Si no se utiliza la opción \/transparent, PEVerify también comprueba los métodos críticos que pueden contener código no comprobable.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, marque el método con el atributo <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityCriticalAttribute>, o quite el código no comprobable.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El método de este ejemplo utiliza el código no comprobable y se debe marcar con el atributo <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityCriticalAttribute>.  
  
 [!code-cs[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]