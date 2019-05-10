---
title: No se puede crear una asociación; la propiedad aparece más de una vez.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fcc2a7322397537c9585d0aaa2674e1d3ab3c656
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460698"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>No se puede crear una asociación &lt;nombre de asociación&gt;; la propiedad aparece dos veces.

No se puede crear una asociación \<nombre de asociación>. La misma propiedad aparece más de una vez: \<nombre de propiedad>.

Las asociaciones las define el comando **Propiedades de la asociación** seleccionado en el cuadro de diálogo **Editor de asociaciones**. Las propiedades pueden aparecer solamente una vez para cada clase en la asociación.

La propiedad mencionada en el mensaje aparece más de una vez en las **Propiedades de la asociación** de la clase primaria o secundaria.

## <a name="to-resolve-this-condition"></a>Para resolver esta condición

- Lea el mensaje y fíjese en la propiedad especificada en el mensaje.

- Haga clic en **Aceptar** para descartar el cuadro de mensaje.

- Examine las **Propiedades de la asociación** y quite las entradas duplicadas.

- Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)
- [Cómo: Crear una asociación entre clases LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)