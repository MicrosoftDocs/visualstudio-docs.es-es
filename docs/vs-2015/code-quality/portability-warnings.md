---
title: Advertencias de portabilidad | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3b7c38f8380fc8e52707b9c4817880b1ce86b4b9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173087"
---
# <a name="portability-warnings"></a>advertencias de portabilidad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Advertencias de portabilidad compatibles con la portabilidad entre diferentes sistemas operativos.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Regla|Descripción|  
|----------|-----------------|  
|[CA1900: Los campos de tipo de valor deberían ser portátiles](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Esta regla comprueba que las estructuras declaradas mediante un atributo de diseño explícito se alinearán correctamente cuando se calculan las referencias a código no administrado en sistemas operativos de 64 bits.|  
|[CA1901: Las declaraciones P/Invoke deben ser portables](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Esta regla se evalúa como el tamaño de cada parámetro y el valor devuelto de P/Invoke y comprueba que su tamaño sea correcto al calcular las referencias a código no administrado en sistemas operativos de 32 bits y 64 bits.|  
|[CA1903: Usar solo API de la versión de .NET Framework de destino](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Un miembro o tipo utiliza un miembro o tipo que se introdujo en un Service Pack no incluido junto con la versión de .NET Framework de destino del proyecto.|



