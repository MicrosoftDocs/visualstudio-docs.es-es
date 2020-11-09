---
title: La propiedad se muestra dos veces
description: No se puede crear una lista de propiedades de asociación dos veces. Vea información sobre este mensaje de Object Relational Designer de Visual Studio (Object Relational Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.technology: vs-data-tools
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d4cb795a5d608e31c26ccec0b96f359a5c63cee7
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2020
ms.locfileid: "94381784"
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