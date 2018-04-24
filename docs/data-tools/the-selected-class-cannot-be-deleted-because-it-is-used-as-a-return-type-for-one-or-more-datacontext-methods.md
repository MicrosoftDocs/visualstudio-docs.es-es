---
title: No se puede eliminar la clase seleccionada porque se usa como tipo devuelto de uno o varios métodos DataContext
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c1460f8e3484633643d5b7bc9c7df181989b83ff
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>No se puede eliminar la clase seleccionada porque se usa como tipo devuelto de uno o varios métodos DataContext

El tipo de valor devuelto de uno o varios métodos de <xref:System.Data.Linq.DataContext> es la clase de entidad seleccionada. Cuando se elimina una clase de entidad que se usa como tipo de valor devuelto para un método de <xref:System.Data.Linq.DataContext>, se pueden producir errores en la compilación del proyecto. Para eliminar la clase de entidad seleccionada, identifique los métodos de <xref:System.Data.Linq.DataContext> que la usan y establezca sus tipos de valor devuelto en otra clase de entidad.

Para revertir los tipos de valor devueltos de <xref:System.Data.Linq.DataContext> métodos a sus tipos originales generados automáticamente, primero debe eliminar el <xref:System.Data.Linq.DataContext> método desde el panel de métodos y, a continuación, arrastre el objeto desde **Explorador de servidores** / **El Explorador de base de datos** hasta Object Relational Designer.

## <a name="to-correct-this-error"></a>Para corregir este error

1. Identificar <xref:System.Data.Linq.DataContext> métodos que usan la clase de entidad como un tipo de valor devuelto, seleccione un <xref:System.Data.Linq.DataContext> método en los métodos de panel e inspeccionando el **tipo de valor devuelto** propiedad en el **propiedades** ventana .

2. Establecer el **tipo de valor devuelto** en otra clase de entidad o elimine la <xref:System.Data.Linq.DataContext> método desde el panel de métodos.

## <a name="see-also"></a>Vea también

- [Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL de las herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)