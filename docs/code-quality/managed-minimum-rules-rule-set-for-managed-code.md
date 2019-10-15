---
title: Conjunto de reglas Reglas mínimas administradas para código administrado
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc3d0376e0f3af186802fa566e1618ae7ed89a78
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305606"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas mínimas administradas para código administrado

Las reglas mínimas administradas se centran en los problemas más críticos del código, incluidas posibles vulnerabilidades de seguridad, bloqueos de la aplicación y otros errores de diseño y lógica importantes. Incluya este conjunto de reglas en cualquier conjunto de reglas personalizado que cree para sus proyectos.

|Regla|Descripción|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Los tipos que poseen campos descartables deben ser descartables|
|[CA1821](../code-quality/ca1821.md)|Quitar finalizadores vacíos|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Los campos descartables deben ser descartables|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Sobrecargar el operador de igualdad al reemplazar `ValueType.Equals`|
