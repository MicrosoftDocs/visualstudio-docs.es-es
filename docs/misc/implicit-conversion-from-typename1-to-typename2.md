---
title: "Conversi&#243;n impl&#237;cita de &#39;&lt;nombreDeTipo1&gt;&#39; a &#39;&lt;nombreDeTipo2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42016"
  - "BC42016"
helpviewer_keywords: 
  - "BC42016"
ms.assetid: 7dabaab0-8258-4c17-927f-28e61f50bd3a
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conversi&#243;n impl&#237;cita de &#39;&lt;nombreDeTipo1&gt;&#39; a &#39;&lt;nombreDeTipo2&gt;&#39;
Una expresión o una instrucción de asignación toma un valor de un tipo de datos y lo convierte a otro tipo. Dado que no se usa ninguna palabra clave de conversión, la conversión es *implícita*.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42016  
  
### Para corregir este error  
  
-   Si es posible, use valores del mismo tipo de datos, de modo que [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no tengan que realizar ninguna conversión.  
  
-   Use `CType` o una de las otras palabras clave de conversión para que la conversión sea *explícita*.  
  
## Vea también  
 [Conversiones implícitas y explícitas](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Funciones de conversión de tipos](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)