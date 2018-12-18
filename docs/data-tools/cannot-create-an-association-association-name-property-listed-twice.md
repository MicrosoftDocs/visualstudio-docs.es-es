---
title: No se puede crear una asociación - propiedad aparece dos veces
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d508cc407087e481ff77e29956db7511bba81165
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916834"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>No se puede crear una asociación &lt;nombre de la asociación&gt; -propiedad aparece dos veces

No se puede crear una asociación \<nombre de asociación >. La misma propiedad aparece más de una vez: \<nombre de propiedad >.

Las asociaciones se definen por seleccionado **propiedades de la asociación** en el **Editor de asociaciones** cuadro de diálogo. Las propiedades pueden aparecer solamente una vez para cada clase en la asociación.

La propiedad en el mensaje aparece más de una vez en primaria o secundaria de la clase **propiedades de la asociación**.

## <a name="to-resolve-this-condition"></a>Para resolver esta condición

- Lea el mensaje y fíjese en la propiedad especificada en el mensaje.

- Haga clic en **Aceptar** para descartar el cuadro de mensaje.

- Inspeccionar el **propiedades de la asociación** y quite las entradas duplicadas.

- Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también

- [Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL de las herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Cómo: crear una asociación entre clases LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)