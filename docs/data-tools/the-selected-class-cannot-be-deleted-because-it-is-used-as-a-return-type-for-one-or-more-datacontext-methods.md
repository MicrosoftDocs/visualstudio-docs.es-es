---
title: No se puede eliminar la clase seleccionada
description: No se puede eliminar la clase seleccionada porque se usa como tipo devuelto de uno o varios métodos DataContext
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: a9948df37df4faf7cc5349b2729ca4f648d973cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866390"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>No se puede eliminar la clase seleccionada porque se usa como tipo devuelto de uno o varios métodos DataContext

El tipo de valor devuelto de uno o varios métodos de <xref:System.Data.Linq.DataContext> es la clase de entidad seleccionada. Al eliminar una clase de entidad que se usa como tipo de valor devuelto para un <xref:System.Data.Linq.DataContext> método, se produce un error en la compilación del proyecto. Para eliminar la clase de entidad seleccionada, identifique los métodos de <xref:System.Data.Linq.DataContext> que la usan y establezca sus tipos de valor devuelto en otra clase de entidad.

Para revertir los tipos de valor devuelto de los métodos de <xref:System.Data.Linq.DataContext> a sus tipos originales generados automáticamente, primero elimine el método de <xref:System.Data.Linq.DataContext> del panel **Métodos** y después arrastre el objeto desde el **Explorador de servidores**/**Explorador de bases de datos** hasta **Object Relational Designer**.

## <a name="to-correct-this-error"></a>Para corregir este error

1. Para identificar los métodos de <xref:System.Data.Linq.DataContext> que usan la clase de entidad como tipo de valor devuelto, seleccione un método de <xref:System.Data.Linq.DataContext> en el panel **Métodos** y examine la propiedad **Tipo devuelto** en la ventana **Propiedades**.

2. Establezca **Tipo devuelto** en otra clase de entidad o elimine el método de <xref:System.Data.Linq.DataContext> del panel de métodos.

## <a name="see-also"></a>Vea también

- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
