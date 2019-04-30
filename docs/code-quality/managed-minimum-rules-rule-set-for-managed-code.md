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
ms.openlocfilehash: eb9078050b42998bb88ad71580ecd506b9049f86
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825382"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Conjunto de reglas Reglas mínimas administradas para código administrado

Las reglas administrado mínimo se centran en los problemas más graves del código, incluidas posibles vulnerabilidades de seguridad, bloqueos de la aplicación y otros errores de diseño y lógica importantes. Incluir este conjunto de reglas en cualquier conjunto de reglas personalizados que cree para sus proyectos.

|Regla|Descripción|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Los tipos que poseen campos descartables deben ser descartables|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Quitar finalizadores vacíos|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Los campos descartables deben ser descartables|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Sobrecargar el operador equals al invalidar ValueType.Equals|
