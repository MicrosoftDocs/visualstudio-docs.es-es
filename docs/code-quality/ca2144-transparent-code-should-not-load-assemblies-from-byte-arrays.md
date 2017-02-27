---
title: "CA2144: El c&#243;digo transparente no debe cargar ensamblados desde matrices de bytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2144"
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA2144: El c&#243;digo transparente no debe cargar ensamblados desde matrices de bytes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|  
|Identificador de comprobación|CA2144|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método transparente carga un ensamblado desde una matriz de bytes utilizando uno de los métodos siguientes:  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
## Descripción de la regla  
 La revisión de seguridad del código transparente no es tan exhaustiva como la revisión de seguridad del código crítico, porque el código transparente no puede realizar acciones que afectan a la seguridad.  Los ensamblados cargados desde una matriz de bytes podrían no distinguirse en el código transparente, y esa matriz de bytes podría contener código importante crítico para la seguridad, que no hace falta auditar.  Por consiguiente, el código transparente no debería cargar los ensamblados de una matriz de bytes.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, marque el método que está cargando el ensamblado con el atributo <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityCriticalAttribute>.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 La regla se desencadena en el código siguiente porque un método transparente carga un ensamblado de una matriz de bytes.  
  
 [!code-cs[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]