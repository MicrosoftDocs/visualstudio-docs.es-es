---
title: "Solucionar problemas de m&#233;tricas de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 4
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
caps.handback.revision: 4
---
# Solucionar problemas de m&#233;tricas de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Al recopilar métricas de código, podría experimentar algunos de los siguientes problemas:  
  
-   [Cambios en cálculos de complejidad de código de Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Cambios en cálculos de complejidad de código de Visual Studio 2010  
 Para la misma función, la métrica de complejidad de código calculada en [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] puede ser diferente de la calculada por versiones anteriores de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] en las siguientes situaciones:  
  
-   La función contiene uno o más bloques catch.  En versiones anteriores de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], los bloques catch no se incluían en el cálculo.  En [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], la complejidad de cada bloque catch se agrega a la complejidad de la función.  
  
-   La función contiene una instrucción Switch \(Select Case en VB\).  Las diferencias del compilador entre [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] y versiones anteriores pueden generar código MSIL diferente para algunas instrucciones Switch que contienen casos de paso explícito.  
  
## Vea también  
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)