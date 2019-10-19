---
title: Uno o varios elementos seleccionados contienen un tipo de datos que el diseñador no admite
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 036026d7640dc525538191d2acc347e9ba18b871
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648259"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Uno o varios elementos seleccionados contienen un tipo de datos que el diseñador no admite

Uno o varios de los elementos arrastrados desde **Explorador de servidores** o **Explorador de bases de datos** hasta **Object** Relational Designer contiene un tipo de datos no admitido por Object Relational **Designer**, por ejemplo, los [tipos definidos por el usuario CLR](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Para corregir este error

1. Cree una vista basada en la tabla deseada y que no incluya el tipo de datos no admitidos.

2. Arrastre la vista desde **Explorador de servidores** o **Explorador de bases de datos** al diseñador.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) (Herramientas LINQ to SQL en Visual Studio)