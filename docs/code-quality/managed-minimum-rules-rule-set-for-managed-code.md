---
title: Conjunto de reglas Reglas mínimas administradas para código administrado
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 903b464172d541277de5fbac6d8ab035578b6154
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658508"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas mínimas administradas para código administrado

Las reglas mínimas administradas se centran en los problemas más críticos del código, incluidas posibles vulnerabilidades de seguridad, bloqueos de la aplicación y otros errores de diseño y lógica importantes. Incluya este conjunto de reglas en cualquier conjunto de reglas personalizado que cree para sus proyectos.

|Regla|Descripción|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Los tipos que poseen campos descartables deben ser descartables|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Quitar finalizadores vacíos|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Los campos descartables deben ser descartables|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Sobrecargar el operador de igualdad al reemplazar `ValueType.Equals`|
