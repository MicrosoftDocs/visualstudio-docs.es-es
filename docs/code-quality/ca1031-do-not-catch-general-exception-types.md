---
title: "CA1031: No capturar los tipos de excepci&#243;n general | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1031"
  - "DoNotCatchGeneralExceptionTypes"
helpviewer_keywords: 
  - "CA1031"
  - "DoNotCatchGeneralExceptionTypes"
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1031: No capturar los tipos de excepci&#243;n general
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotCatchGeneralExceptionTypes|  
|Identificador de comprobación|CA1031|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Una excepción general como <xref:System.Exception?displayProperty=fullName> o <xref:System.SystemException?displayProperty=fullName> se detecta en una instrucción `catch` o se utiliza una cláusula catch general como `catch()`.  
  
## Descripción de la regla  
 No se deben capturar excepciones generales.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, captura una excepción más específica, o vuelva a producir una excepción general como la última instrucción del bloque `catch`.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Capturar tipos de excepciones generales puede ocultar los problemas en tiempo de ejecución del usuario de la biblioteca y pueden dificultar la depuración.  
  
> [!NOTE]
>  A partir de [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], Common Language Runtime \(CLR\) ya no proporciona excepciones de estado corruptas que aparecen en el sistema operativo y el código administrado, como infracciones de acceso en [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], para ser manejadas mediante código administrado.  Si desea compilar una aplicación en [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] \(o posterior\) y mantener el control de las excepciones de estado corruptas, puede aplicar el atributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> al método que administra la excepción de estado corrupta.  
  
## Ejemplo  
 El ejemplo siguiente muestra un tipo que infringe esta regla y un tipo que implementa correctamente el bloque `catch`.  
  
 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-cs[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]  
  
## Reglas relacionadas  
 [CA2200: Iniciar de nuevo para preservar los detalles de la pila](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)