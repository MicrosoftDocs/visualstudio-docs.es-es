---
title: 'CA1822: Marcar miembros como estáticos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ebbbbe01f1dd23dfc560e019133dacd3517b388
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253458"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Marcar miembros como estáticos

|||
|-|-|
|TypeName|MarkMethodsAsStatic|
|Identificador de comprobación|CA1822|
|Categoría|Microsoft.Performance|
|Cambio importante|No problemático: Si el miembro no es visible fuera del ensamblado, independientemente del cambio que realice. No problemático: si simplemente cambia el miembro a un miembro de instancia con la `this` palabra clave.<br /><br /> Problemático: Si cambia el miembro de un miembro de instancia a un miembro estático y es visible fuera del ensamblado.|

## <a name="cause"></a>Motivo
Un miembro que no tiene acceso a los datos de instancia no está marcado como estático [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)](compartido en).

## <a name="rule-description"></a>Descripción de la regla
Los miembros que no tienen acceso a datos de instancia o que llaman a métodos de instancia se pueden marcar como static (Shared en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Después de marcar los métodos como static, el compilador emite los sitios de llamada no virtuales para estos miembros. La emisión de sitios de llamada no virtuales impedirá una comprobación en tiempo de ejecución para cada llamada que se asegure de que el puntero del objeto actual no es NULL. Esto puede lograr una mejora de rendimiento mensurable para el código que depende del rendimiento. En algunos casos, el error de acceso a la instancia del objeto actual representa un problema de corrección.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Marque el miembro como estático (o compartido en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) o use ' this '/' me ' en el cuerpo del método, si procede.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla para el código enviado previamente para el que la corrección sería un cambio importante.

## <a name="related-rules"></a>Reglas relacionadas
[CA1811: Evitar código privado no llamado](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812: Evitar clases internas sin instancias](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1804: Quitar variables locales no usadas](../code-quality/ca1804-remove-unused-locals.md)