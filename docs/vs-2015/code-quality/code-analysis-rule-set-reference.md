---
title: Referencia de conjunto de reglas de análisis de código | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a1f91b352da5a41ec2ef81fb6067976073c787ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62576759"
---
# <a name="code-analysis-rule-set-reference"></a>Referencia del conjunto de reglas Análisis de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al configurar el análisis de código para proyectos de código en administrado [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], o [!INCLUDE[vsPro](../includes/vspro-md.md)]se le presentará una lista de integrados *conjuntos de reglas*. Se puede usar uno de los conjuntos de reglas estándar o bien personalizar un conjunto de reglas para ajustarse a los requisitos del proyecto.  
  
## <a name="available-rule-sets"></a>Conjuntos de reglas disponibles  
 En la tabla siguiente se enumeran los conjuntos de reglas predeterminados:  
  
|||  
|-|-|  
|[Conjunto de reglas Todas las reglas](../code-quality/all-rules-rule-set.md)|Este conjunto de reglas contiene todas las reglas. Si se ejecuta este conjunto de reglas, puede dar lugar a un gran número de advertencias. Use este conjunto de reglas para obtener una imagen completa de todos los problemas del código. Esto puede ser útil para decidir qué conjuntos de reglas son más apropiados para ejecutarlos para sus proyectos.|  
|[Conjunto de reglas Reglas de corrección básicas para código administrado](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Estas reglas se centran en errores lógicos y comunes cometidos en el uso de API de marco de trabajo. Incluya este conjunto de reglas para ampliar la lista de advertencias emitidas por las reglas mínimas recomendadas.|  
|[Conjunto de reglas Reglas de directrices de diseño básicas para código administrado](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Estas reglas se centran en exigir procedimientos recomendados para que el código sea fácil de comprender y de usar. Incluya este conjunto de reglas si el proyecto incluye código de bibliotecas o si desea exigir procedimientos recomendados para que el código sea fácil de mantener.|  
|[Conjunto de reglas Reglas de corrección extendidas para código administrado](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Estas reglas amplían las reglas de corrección básicas con el fin de maximizar los errores de lógica y uso del marco de trabajo que se detectan. Se pone especial énfasis en escenarios específicos como la interoperabilidad COM y las aplicaciones móviles. Considere incluir este conjunto de reglas si alguno de estos escenarios es aplicable a su proyecto o para buscar problemas adicionales del proyecto.|  
|[Conjunto de reglas Reglas de directrices de diseño ampliadas para código administrado](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Estas reglas amplían las reglas de directrices de diseño básicas con el fin de maximizar los problemas de uso y mantenimiento que se detectan. Se pone especial énfasis en las directrices de nomenclatura. Considere incluir este conjunto de reglas si el proyecto incluye código de bibliotecas o si desea exigir los más altos estándares para escribir código fácil de mantener.|  
|[Conjunto de reglas Reglas de globalización para código administrado](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Estas reglas se centran en problemas que impiden que los datos de la aplicación se muestren correctamente cuando se usan en diferentes idiomas, configuraciones regionales y referencias culturales. Incluya este conjunto de reglas si la aplicación se localiza o globaliza.|  
|[Conjunto de reglas Reglas mínimas administradas para código administrado](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Estas reglas se centran en los problemas más graves del código para los que el análisis del mismo es la solución más precisa.  Estas reglas son pocas y están destinadas a ejecutarse solamente en ediciones limitadas de Visual Studio.  Use MinimumRecommendedRules.ruleset con otras ediciones de Visual Studio.|  
|[Conjunto de reglas Reglas recomendadas administradas para código administrado](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Estas reglas se centran en los problemas más graves del código, incluidas posibles vulnerabilidades de seguridad, bloqueos de la aplicación y otros errores de diseño y lógica importantes. Debe incluir este conjunto de reglas en todos los conjuntos de reglas personalizados que cree para sus proyectos.|  
|[Conjunto de reglas Reglas mínimas mixtas](../code-quality/mixed-minimum-rules-rule-set.md)|Estas reglas se centran en los problemas más graves de los proyectos de C++ compatibles con Common Language Runtime, incluidas posibles vulnerabilidades de seguridad y bloqueos de la aplicación. Debe incluir este conjunto de reglas en todos los conjuntos de reglas personalizados que cree para sus proyectos de C++ compatibles con Common Language Runtime.|  
|[Conjunto de reglas Reglas recomendadas mixtas](../code-quality/mixed-recommended-rules-rule-set.md)|Estas reglas se centran en los problemas más graves y habituales de los proyectos de C++ compatibles con Common Language Runtime, incluidas posibles vulnerabilidades de seguridad, bloqueos de la aplicación y otros errores de diseño y lógica importantes. Debe incluir este conjunto de reglas en todos los conjuntos de reglas personalizados que cree para sus proyectos de C++ compatibles con Common Language Runtime.  Este conjunto de reglas está diseñado para configurarse con Visual Studio Professional y versiones posteriores.|  
|[Conjunto de reglas Reglas mínimas nativas](../code-quality/native-minimum-rules-rule-set.md)|Estas reglas se centran en los problemas más graves del código nativo, incluidas posibles vulnerabilidades de seguridad y bloqueos de la aplicación. Debe incluir este conjunto de reglas en todos los conjuntos de reglas personalizados que cree para sus proyectos nativos.|  
|[Conjunto de reglas Reglas recomendadas nativas](../code-quality/native-recommended-rules-rule-set.md)|Estas reglas se centran en los problemas más graves y habituales del código nativo, incluidas posibles vulnerabilidades de seguridad y bloqueos de la aplicación.  Debe incluir este conjunto de reglas en todos los conjuntos de reglas personalizados que cree para sus proyectos nativos.  Este conjunto de reglas está diseñado para funcionar con Visual Studio Professional y versiones posteriores.|  
|[Conjunto de reglas Reglas de seguridad para código administrado](../code-quality/security-rules-rule-set-for-managed-code.md)|Este conjunto de reglas contiene todas las reglas de seguridad de Microsoft. Incluya este conjunto de reglas para maximizar el número de posibles problemas de seguridad que se detectan.|
