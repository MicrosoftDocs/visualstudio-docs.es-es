---
title: No se puede eliminar la clase seleccionada porque se usa como tipo devuelto de uno o varios métodos DataContext
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 21ef0f86d701c899328044a03cde8035a1e7292d
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174216"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>No se puede eliminar la clase seleccionada porque se usa como tipo devuelto de uno o varios métodos DataContext

El tipo de valor devuelto de uno o varios métodos de <xref:System.Data.Linq.DataContext> es la clase de entidad seleccionada. Eliminación de una clase de entidad que se usa como el tipo de valor devuelto para un <xref:System.Data.Linq.DataContext> método hace que la compilación del proyecto que se producirá un error. Para eliminar la clase de entidad seleccionada, identifique los métodos de <xref:System.Data.Linq.DataContext> que la usan y establezca sus tipos de valor devuelto en otra clase de entidad.

Para revertir los tipos de valor devueltos de <xref:System.Data.Linq.DataContext> métodos a los tipos originales generados automáticamente, primero debe eliminar el <xref:System.Data.Linq.DataContext> método desde el **métodos** panel y, a continuación, arrastre el objeto desde **Explorador de servidores** / **Database Explorer** hasta la **Object Relational Designer** nuevo.

## <a name="to-correct-this-error"></a>Para corregir este error

1. Identificar <xref:System.Data.Linq.DataContext> métodos que usan la clase de entidad como un tipo de valor devuelto seleccionando un <xref:System.Data.Linq.DataContext> método en el **métodos** panel e inspeccionando el **tipo de valor devuelto** propiedad en el **Propiedades** ventana.

2. Establecer el **Return Type** con otra clase de entidad o elimine la <xref:System.Data.Linq.DataContext> método desde el panel de métodos.

## <a name="see-also"></a>Vea también

- [Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)