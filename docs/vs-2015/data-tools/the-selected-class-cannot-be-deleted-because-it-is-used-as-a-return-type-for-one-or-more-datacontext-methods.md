---
title: No se puede eliminar la clase seleccionada porque se usa como tipo de valor devuelto para uno o varios métodos DataContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf16fe7453388e19308ed603ee9dbbac207cec41
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667260"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>No se puede eliminar la clase seleccionada porque se usa como tipo devuelto de uno o varios métodos DataContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El tipo de valor devuelto de uno o varios métodos de <xref:System.Data.Linq.DataContext> es la clase de entidad seleccionada. Cuando se elimina una clase de entidad que se usa como tipo de valor devuelto para un método de <xref:System.Data.Linq.DataContext>, se pueden producir errores en la compilación del proyecto. Para eliminar la clase de entidad seleccionada, identifique los métodos de <xref:System.Data.Linq.DataContext> que la usan y establezca sus tipos de valor devuelto en otra clase de entidad.

 Para revertir los tipos de valor devueltos de <xref:System.Data.Linq.DataContext> métodos a sus tipos generados automáticamente originales, elimine primero el método <xref:System.Data.Linq.DataContext> del panel métodos y, a continuación, arrastre el objeto desde **Explorador de servidores** /**Explorador de bases de datos** al Object Relational Designer.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Identifique <xref:System.Data.Linq.DataContext> métodos que usan la clase de entidad como un tipo de valor devuelto; para ello, seleccione un método de <xref:System.Data.Linq.DataContext> en el panel métodos e inspeccione la propiedad **tipo de valor devuelto** en la ventana **propiedades** .

2. Establezca **Tipo devuelto** en otra clase de entidad o elimine el método de <xref:System.Data.Linq.DataContext> del panel de métodos.

## <a name="see-also"></a>Vea también
 [LINQ to SQL herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [Tutorial: crear clases de LINQ to SQL (Object Relational Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md) [Cómo: cambiar el tipo de valor devuelto de un método DataContext (Object](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md) Relational Designer)
