---
title: No se puede crear una asociación; la propiedad aparece más de una vez.
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 92999e211ec0f7265f026446e09dbc94cc3060f3
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282805"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>No se puede crear una asociación &lt;nombre de asociación&gt;; la propiedad aparece dos veces.

No se puede crear una asociación \<association name> . La misma propiedad aparece más de una vez: \<property name> .

Las asociaciones las define el comando **Propiedades de la asociación** seleccionado en el cuadro de diálogo **Editor de asociaciones**. Las propiedades pueden aparecer solamente una vez para cada clase en la asociación.

La propiedad mencionada en el mensaje aparece más de una vez en las **Propiedades de la asociación** de la clase primaria o secundaria.

## <a name="to-resolve-this-condition"></a>Para resolver esta condición

- Lea el mensaje y fíjese en la propiedad especificada en el mensaje.

- Haga clic en **Aceptar** para descartar el cuadro de mensaje.

- Examine las **Propiedades de la asociación** y quite las entradas duplicadas.

- Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también

- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Cómo: crear una asociación entre clases LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)