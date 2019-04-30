---
title: Uno o varios elementos seleccionados contienen un tipo de datos que el diseñador no admite
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 12ec2ed7dc2a12556fcb6eeeddbe2d0745ae7f72
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566373"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Uno o varios elementos seleccionados contienen un tipo de datos que el diseñador no admite

Uno o varios de los elementos arrastran desde **Explorador de servidores** o **Database Explorer** hasta la **Object Relational Designer** contiene un tipo de datos que no es compatible con la **O /R diseñador**, por ejemplo, [tipos definidos por el usuario CLR](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Para corregir este error

1. Cree una vista basada en la tabla deseada y que no incluya el tipo de datos no admitidos.

2. Arrastre la vista del **Explorador de servidores** o **Database Explorer** hasta el diseñador.

## <a name="see-also"></a>Vea también

- [Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)