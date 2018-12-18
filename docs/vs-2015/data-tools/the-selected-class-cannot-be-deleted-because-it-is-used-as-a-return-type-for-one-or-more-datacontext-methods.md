---
title: La clase seleccionada no se puede eliminar porque se utiliza como un tipo de valor devuelto de uno o varios métodos DataContext | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 084843636d62bd7d85c5bbc141aa0fe8ddf81462
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236267"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>No se puede eliminar la clase seleccionada porque se usa como tipo devuelto de uno o varios métodos DataContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
El tipo de valor devuelto de uno o varios métodos de <xref:System.Data.Linq.DataContext> es la clase de entidad seleccionada. Cuando se elimina una clase de entidad que se usa como tipo de valor devuelto para un método de <xref:System.Data.Linq.DataContext>, se pueden producir errores en la compilación del proyecto. Para eliminar la clase de entidad seleccionada, identifique los métodos de <xref:System.Data.Linq.DataContext> que la usan y establezca sus tipos de valor devuelto en otra clase de entidad.  
  
 Para revertir los tipos de valor devueltos de <xref:System.Data.Linq.DataContext> métodos a los tipos originales generados automáticamente, primero debe eliminar el <xref:System.Data.Linq.DataContext> método desde el panel de métodos y, a continuación, arrastre el objeto desde **Explorador de servidores** / **Database Explorer** en el Object Relational Designer nuevo.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Identificar <xref:System.Data.Linq.DataContext> métodos que usan la clase de entidad como un tipo de valor devuelto seleccionando un <xref:System.Data.Linq.DataContext> método en los métodos de panel e inspeccionar el **tipo devuelto** propiedad en el **propiedades** ventana .  
  
2.  Establecer el **Return Type** con otra clase de entidad o elimine la <xref:System.Data.Linq.DataContext> método desde el panel de métodos.  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Cómo: Cambiar el tipo de valor devuelto de un método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)

