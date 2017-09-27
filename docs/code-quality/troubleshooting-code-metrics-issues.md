---
title: "Solucionar problemas de métricas de código | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: ea1e787c1d509123a650cf2bd20e5fa8bffd5b4e
ms.openlocfilehash: 9f3f41548412d84cd1219aae45b7c87ea5383de9
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="troubleshooting-code-metrics-issues"></a>Solucionar problemas de métricas de código
Pueden surgir algunos de los siguientes problemas al recopilar métricas de código:  
  
-   [Cambios en los cálculos de complejidad de código de Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Cambios en los cálculos de complejidad de código de Visual Studio 2010  
 Para la misma función, la métrica de complejidad de código se calcula en [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] puede ser diferente de la métrica calculada por versiones anteriores de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] en las siguientes situaciones:  
  
-   La función contiene uno o varios bloques catch. En versiones anteriores de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], catch bloques no se incluyeron en el cálculo. En [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], la complejidad de cada bloque catch se agrega a la complejidad de la función.  
  
-   La función contiene una instrucción switch (Select Case en VB). Compilador diferencias entre [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] y versiones anteriores pueden generar código MSIL diferente para algunas instrucciones switch que contienen casos de paso explícito.  
  
## <a name="see-also"></a>Vea también  
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
