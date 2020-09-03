---
title: Sintaxis de la ruta de acceso del dominio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
ms.assetid: 945994f9-72b9-42e0-81b2-e5fb3d0e282d
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b25b47b5b711f09334501ed21abf06cb66402b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669741"
---
# <a name="domain-path-syntax"></a>Sintaxis de las rutas de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las definiciones de DSL usan una sintaxis del estilo de XPath para ubicar elementos específicos en un modelo.

 Normalmente no tiene que trabajar con esta sintaxis directamente. Cuando aparece en las ventanas DSL Details (Detalles de DSL) o Properties (Propiedades), puede hacer clic en la flecha hacia abajo y usar el editor de rutas. Sin embargo, la ruta aparece con este formato en el campo después de haber usado el editor.

 Una ruta de dominio adopta el formato siguiente:

 *NombreRelación.NombrePropiedad/!Rol*

 ![Relación de referencia CommentReferencesSubjects](../modeling/media/dsl-reference.png "dsl_reference")

 La sintaxis atraviesa el árbol del modelo. Por ejemplo, la relación de dominio **CommentReferencesSubjects** de la ilustración anterior tiene un rol **asuntos** . La ruta de acceso Segment **/! Subjectt** especifica que la ruta de acceso finaliza en los elementos a los que se accede a través del rol de **sujetos** .

 Cada segmento comienza con el nombre de una relación de dominio. Si el recorrido proviene de un elemento a una relación, el segmento de ruta de acceso aparece como *Relationship. PropertyName*. Si el salto es de un vínculo a un elemento, el segmento de ruta de acceso aparece como *Relationship/! RoleName*.

 La sintaxis de una ruta se separa con barras inclinadas. Cada segmento de ruta es un salto desde un elemento a un vínculo (una instancia de una relación) o desde un vínculo a un elemento. Los segmentos de ruta suelen aparecer en parejas. Un segmento de ruta representa un salto desde un elemento a un vínculo, y el siguiente representa un salto desde el vínculo al elemento del otro extremo. (Un vínculo puede ser también origen o destino de una relación).

 El nombre que use para el salto elemento-vínculo es el valor de `Property Name` del rol. El nombre que use para el salto vínculo-elemento es el nombre del rol de destino.

## <a name="see-also"></a>Consulte también
 [Introducción a los modelos, las clases y las relaciones](../modeling/understanding-models-classes-and-relationships.md)
