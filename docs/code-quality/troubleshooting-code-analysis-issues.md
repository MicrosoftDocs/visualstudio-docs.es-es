---
title: Solucionar problemas de análisis de código
ms.date: 11/04/2016
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 936428b82e721a1df6003a4bb0eecefe5b696b4c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825356"
---
# <a name="troubleshooting-code-analysis-issues"></a>Solucionar problemas de análisis de código
Este tema contiene información para solucionar los siguientes problemas de análisis de código de Visual Studio.

- [Los cambios en un conjunto de reglas de Visual Studio 2010 no se reflejan en las versiones anteriores de Visual Studio](#ChildRuleSetChangesInPreviousVersions)

## <a name="ChildRuleSetChangesInPreviousVersions"></a> Los cambios en un conjunto de reglas de Visual Studio 2010 no se reflejan en las versiones anteriores de Visual Studio
 Cuando se crea un conjunto de reglas en [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] que contiene un conjunto de reglas secundario, es posible que no se pueda aplicar un cambio en dicho conjunto de reglas secundario en ejecuciones de análisis de código desde equipos que utilizan una versión anterior de Visual Studio. Para resolver este problema, debe forzar una reescritura del conjunto de reglas primario, que es el conjunto de reglas que contiene el conjunto de reglas secundario.

1. Abra el conjunto de reglas primario establecido en [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].

2. Realice un cambio, como agregar o eliminar una regla y, después, guarde el conjunto de reglas.

3. Vuelva a abrir el conjunto de reglas, invierta el cambio y guarde de nuevo el conjunto de reglas.

## <a name="see-also"></a>Vea también

- [Analizar la calidad de la aplicación](../code-quality/code-analysis-for-managed-code-overview.md)
- [Analizar la calidad del código administrado](../code-quality/code-analysis-for-managed-code-overview.md)
- [Usar conjuntos de reglas para agrupar reglas de análisis de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)