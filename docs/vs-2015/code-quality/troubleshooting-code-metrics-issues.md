---
title: Solucionar problemas de métricas de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4d374a2737e2ce8892304b615bebcf99d9c60ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672455"
---
# <a name="troubleshooting-code-metrics-issues"></a>Solucionar problemas de métricas de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pueden surgir algunos de los problemas siguientes al recopilar métricas del código:

- [Cambios en los cálculos de complejidad de código de Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

## <a name="changes-in-visual-studio-2010-code-complexity-calculations"></a><a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Cambios en los cálculos de complejidad de código de Visual Studio 2010
 Para la misma función, la métrica de complejidad de código calculada en [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] puede ser diferente de la métrica calculada en versiones anteriores de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] en las siguientes situaciones:

- La función contiene uno o varios bloques catch. En versiones anteriores de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], los bloques catch no se incluían en el cálculo. En [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], la complejidad de cada bloque catch se agrega a la complejidad de la función.

- La función contiene una instrucción switch (Select Case en VB). Las diferencias del compilador entre [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] y versiones anteriores pueden generar código MSIL diferente para algunas instrucciones switch que contienen casos de paso explícito.

## <a name="see-also"></a>Consulte también
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
