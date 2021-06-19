---
title: Sintaxis de las rutas de dominio
description: Obtenga información sobre la sintaxis de ruta de acceso de dominio y cómo las definiciones de DSL usan una sintaxis similar a XPath para buscar elementos específicos en un modelo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 69dfd02dca5ead65d4f36303e547aaeba04cde98
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389103"
---
# <a name="domain-path-syntax"></a>Sintaxis de las rutas de dominio
Las definiciones de DSL usan una sintaxis del estilo de XPath para ubicar elementos específicos en un modelo.

 Normalmente no tiene que trabajar con esta sintaxis directamente. Cuando aparece en las ventanas DSL Details (Detalles de DSL) o Properties (Propiedades), puede hacer clic en la flecha hacia abajo y usar el editor de rutas. Sin embargo, la ruta aparece con este formato en el campo después de haber usado el editor.

 Una ruta de dominio adopta el formato siguiente:

 *NombreRelación.NombrePropiedad/!Rol*

 ![Relación de referencia CommentReferencesSubjects](../modeling/media/dsl_reference.png)

 La sintaxis atraviesa el árbol del modelo. Por ejemplo, la relación de dominio **CommentReferencesSubjects** de la ilustración anterior tiene un **rol Subjects.** Segmento de ruta **de acceso /! Subjectt** especifica que la ruta de acceso finaliza en los elementos a los que se accede a través del **rol Subjects.**

 Cada segmento comienza con el nombre de una relación de dominio. Si el recorrido es de un elemento a una relación, el segmento de ruta de acceso aparece *como Relationship.PropertyName*. Si el salto es de un vínculo a un elemento, el segmento de ruta de acceso aparece *como Relationship/! RoleName*.

 La sintaxis de una ruta se separa con barras inclinadas. Cada segmento de ruta es un salto desde un elemento a un vínculo (una instancia de una relación) o desde un vínculo a un elemento. Los segmentos de ruta suelen aparecer en parejas. Un segmento de ruta representa un salto desde un elemento a un vínculo, y el siguiente representa un salto desde el vínculo al elemento del otro extremo. (Un vínculo puede ser también origen o destino de una relación).

 El nombre que use para el salto elemento-vínculo es el valor de `Property Name` del rol. El nombre que use para el salto vínculo-elemento es el nombre del rol de destino.

## <a name="see-also"></a>Vea también

- [Introducción a los modelos, las clases y las relaciones](../modeling/understanding-models-classes-and-relationships.md)
