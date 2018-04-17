---
title: Uno o más elementos seleccionados contienen un tipo de datos que no es compatible con el diseñador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 966adc7a4114c54479c0ad8c52a604e0fb5d3380
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Uno o varios elementos seleccionados contienen un tipo de datos que el diseñador no admite
Uno o varios de los elementos arrastran desde **Explorador de servidores**/**el Explorador de base de datos** en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] contiene un tipo de datos que no es compatible con la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] por ejemplo, [Tipos definidos por el usuario CLR](/dotnet/framework/data/adonet/sql/clr-user-defined-types).  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Cree una vista basada en la tabla deseada y que no incluya el tipo de datos no admitidos.  
  
2.  Arrastre la vista del **Explorador de servidores**/**el Explorador de base de datos** en el diseñador.  
  
## <a name="see-also"></a>Vea también
[Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL de las herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)