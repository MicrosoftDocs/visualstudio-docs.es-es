---
title: 'CA1822: marcar miembros como estáticos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkMembersAsStatic
- CA1822
helpviewer_keywords:
- MarkMembersAsStatic
- CA1822
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a571be6b713cd59ca290906e9398b78c8c021ba8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661167"
---
# <a name="ca1822-mark-members-as-static"></a>CA1822: Marcar el miembro como estático
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente sobre Visual Studio, vea [CA1822: Mark Members as static](https://docs.microsoft.com/visualstudio/code-quality/ca1822-mark-members-as-static).

|||
|-|-|
|TypeName|MarkMethodsAsStatic|
|Identificador de comprobación|CA1822|
|Categoría|Microsoft. performance|
|Cambio problemático|No problemático: Si el miembro no es visible fuera del ensamblado, independientemente del cambio que realice.<br /><br /> No problemático: si simplemente cambia el miembro a un miembro de instancia con la palabra clave `this`.<br /><br /> Problemático: Si cambia el miembro de un miembro de instancia a un miembro estático y es visible fuera del ensamblado.|

## <a name="cause"></a>Motivo
 Un miembro que no tiene acceso a los datos de instancia no está marcado como estático (compartido en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

## <a name="rule-description"></a>Descripción de la regla
 Los miembros que no tienen acceso a datos de instancia o que llaman a métodos de instancia se pueden marcar como static (Shared en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]). Después de marcar los métodos como static, el compilador emite los sitios de llamada no virtuales para estos miembros. La emisión de sitios de llamada no virtuales impedirá una comprobación en tiempo de ejecución para cada llamada que se asegure de que el puntero del objeto actual no es NULL. Esto puede lograr una mejora de rendimiento mensurable para el código que depende del rendimiento. En algunos casos, el error de acceso a la instancia del objeto actual representa un problema de corrección.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Marque el miembro como estático (o compartido en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) o use ' this '/' me ' en el cuerpo del método, si procede.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla para el código enviado previamente para el que la corrección sería un cambio importante.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)
