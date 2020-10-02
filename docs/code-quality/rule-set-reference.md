---
title: Referencia del conjunto de reglas Análisis de código
ms.date: 04/04/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b20974d2e44661ed7f4a0288ecb9eff82b2035a
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658430"
---
# <a name="code-analysis-rule-set-reference"></a>Referencia del conjunto de reglas Análisis de código

Al configurar el análisis heredado para proyectos de código administrado en Visual Studio, puede elegir en una lista de conjuntos de *reglas*integrados. Algunas reglas se incluyen en más de uno de los conjuntos de reglas integrados; por ejemplo, el conjunto de reglas reglas de corrección básicas incluye reglas que se encuentran en el conjunto de reglas reglas recomendadas administradas.

> [!NOTE]
> Los conjuntos de reglas de esta sección pertenecen al análisis heredado. Para obtener información sobre los conjuntos de reglas disponibles para los paquetes del analizador de código, vea [usar conjuntos de reglas con analizadores de código](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

Puede usar uno de estos conjuntos de reglas integrados o puede [personalizar un conjunto de reglas](../code-quality/how-to-create-a-custom-rule-set.md) para ajustarse a los requisitos del proyecto. Si incluye varios conjuntos de reglas que contienen la misma regla en un conjunto de reglas personalizado, esa regla solo aparece una vez en el conjunto de reglas personalizado.

En los temas de esta sección se describen los conjuntos de reglas integrados y las reglas (o advertencias) que contienen.

| Conjunto de reglas | Reglas incluidas |
| - | - |
| [Todas las reglas](all-rules-rule-set.md) | Contiene todas las reglas de C++ y administradas disponibles |
| [Reglas de corrección básicas](basic-correctness-rules-rule-set-for-managed-code.md) | Incluye reglas recomendadas administradas más reglas para errores lógicos y uso del marco de trabajo |
| [Reglas de corrección extendidas](extended-correctness-rules-rule-set-for-managed-code.md) | Incluye reglas de corrección básicas (que incluyen reglas recomendadas administradas) más reglas para errores de lógica y uso del marco de trabajo. |
| [Reglas de directrices de diseño básicas](basic-design-guideline-rules-rule-set-for-managed-code.md) | Incluye reglas recomendadas administradas y reglas para garantizar que el código sea fácil de leer, comprender y mantener. |
| [Reglas de directrices de diseño extendidas](extended-design-guidelines-rules-rule-set-for-managed-code.md) | Incluye reglas de directrices de diseño básicas (que incluyen reglas recomendadas administradas) más reglas de mantenimiento que se centran en la nomenclatura |
| [Reglas de globalización](globalization-rules-rule-set-for-managed-code.md) | Incluye reglas para problemas de globalización |
| [Reglas mínimas administradas](managed-minimum-rules-rule-set-for-managed-code.md) | Incluye cuatro reglas para problemas críticos de código administrado |
| [Reglas recomendadas administradas](managed-recommended-rules-rule-set-for-managed-code.md) | Incluye reglas mínimas administradas más reglas para problemas críticos de código administrado |
| [Reglas mínimas combinadas](mixed-minimum-rules-rule-set.md) | Incluye reglas para problemas críticos en el código de C++ para CLR |
| [Reglas recomendadas combinadas](mixed-recommended-rules-rule-set.md) | Incluye reglas mínimas mixtas más reglas para problemas críticos en el código de C++ para CLR |
| [Reglas mínimas nativas](native-minimum-rules-rule-set.md) | Incluye reglas para problemas críticos en el código nativo |
| [Reglas recomendadas nativas](native-recommended-rules-rule-set.md) | Incluye reglas mínimas nativas más reglas para problemas críticos en código nativo. |
| [Reglas de seguridad](security-rules-rule-set-for-managed-code.md) | Incluye reglas para buscar vulnerabilidades de seguridad |
