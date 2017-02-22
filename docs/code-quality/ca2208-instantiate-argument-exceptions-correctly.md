---
title: "CA2208: Crear instancias de las excepciones del argumento correctamente | Microsoft Docs"
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
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
helpviewer_keywords: 
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2208: Crear instancias de las excepciones del argumento correctamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InstantiateArgumentExceptionsCorrectly|  
|Identificador de comprobación|CA2208|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Entre las posibles causas se incluyen las siguientes situaciones:  
  
-   Se realiza una llamada al constructor predeterminado \(sin parámetros\) de un tipo de excepción que es o se deriva de [System.ArgumentException](assetId:///System.ArgumentException?qualifyHint=True&autoUpgrade=True).  
  
-   Se pasa un argumento de cadena incorrecto a un constructor con parámetros de un tipo de excepción que es o se deriva de [System.ArgumentException.](assetId:///System.ArgumentException.?qualifyHint=True&autoUpgrade=True)  
  
## Descripción de la regla  
 En lugar de llamar al constructor predeterminado, llame a una de las sobrecargas del constructor que permite proporcionar un mensaje de excepción más significativo.  El mensaje de excepción debería dirigirse al desarrollador y explicar claramente la condición de error y cómo corregir o evitar la excepción.  
  
 Las firmas de uno o dos constructores de cadena de <xref:System.ArgumentException> y sus tipos derivados no son coherentes con respecto a los parámetros `message` y `paramName`.  Asegúrese de que se llama a estos constructores con los argumentos de cadena correctos.  Éstas son las firmas:  
  
 <xref:System.ArgumentException>\(string `message`\)  
  
 <xref:System.ArgumentException>\(string `message`, string `paramName`\)  
  
 <xref:System.ArgumentNullException>\(string `paramName`\)  
  
 <xref:System.ArgumentNullException>\(string `paramName`, string `message`\)  
  
 <xref:System.ArgumentOutOfRangeException>\(string `paramName`\)  
  
 <xref:System.ArgumentOutOfRangeException>\(string `paramName`, string `message`\)  
  
 <xref:System.DuplicateWaitObjectException>\(string `parameterName`\)  
  
 <xref:System.DuplicateWaitObjectException>\(string `parameterName`, string `message`\)  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, llame al constructor que toma un mensaje, un nombre de parámetro, o ambos, y asegúrese de que los argumentos son los adecuados para el tipo de <xref:System.ArgumentException> a la que se llama.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla sólo si se llama a un constructor parametrizado con los argumentos de cadena correctos.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra un constructor que por error crea instancias de una instancia del tipo ArgumentNullException.  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]  
  
## Ejemplo  
 En el ejemplo siguiente se corrige la infracción anterior intercambiando los argumentos del constructor.  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]