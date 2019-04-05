---
title: La clase seleccionada no se puede eliminar porque se utiliza como un tipo de valor devuelto de uno o varios métodos DataContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ad1ccf45a2df6a0b1b23208926136aa2b09eabd3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988785"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>No se puede eliminar la clase seleccionada porque se usa como tipo devuelto de uno o varios métodos DataContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
El tipo de valor devuelto de uno o varios métodos de <xref:System.Data.Linq.DataContext> es la clase de entidad seleccionada. Cuando se elimina una clase de entidad que se usa como tipo de valor devuelto para un método de <xref:System.Data.Linq.DataContext>, se pueden producir errores en la compilación del proyecto. Para eliminar la clase de entidad seleccionada, identifique los métodos de <xref:System.Data.Linq.DataContext> que la usan y establezca sus tipos de valor devuelto en otra clase de entidad.  
  
 Para revertir los tipos de valor devueltos de <xref:System.Data.Linq.DataContext> métodos a los tipos originales generados automáticamente, primero debe eliminar el <xref:System.Data.Linq.DataContext> método desde el panel de métodos y, a continuación, arrastre el objeto desde **Explorador de servidores** / **Database Explorer** en el Object Relational Designer nuevo.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Identificar <xref:System.Data.Linq.DataContext> métodos que usan la clase de entidad como un tipo de valor devuelto seleccionando un <xref:System.Data.Linq.DataContext> método en los métodos de panel e inspeccionar el **tipo devuelto** propiedad en el **propiedades** ventana .  
  
2.  Establezca **Tipo devuelto** en otra clase de entidad o elimine el método de <xref:System.Data.Linq.DataContext> del panel de métodos.  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Cómo: Cambiar el tipo de valor devuelto de un método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)
