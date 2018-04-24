---
title: Uno o varios elementos seleccionados contienen un tipo de datos que el diseñador no admite
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e6aab3e00fc73c14c34e613cd3e3684719f00475
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Uno o varios elementos seleccionados contienen un tipo de datos que el diseñador no admite

Uno o varios de los elementos arrastran desde **Explorador de servidores**/**el Explorador de base de datos** en el [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] contiene un tipo de datos que no es compatible con la [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] por ejemplo, [Tipos definidos por el usuario CLR](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Para corregir este error

1. Cree una vista basada en la tabla deseada y que no incluya el tipo de datos no admitidos.

2. Arrastre la vista del **Explorador de servidores**/**el Explorador de base de datos** en el diseñador.

## <a name="see-also"></a>Vea también

- [Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL de las herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)