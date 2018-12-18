---
title: Uno o varios elementos seleccionados contienen un tipo de datos que el diseñador no admite
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 68d8675df54e37b9a6122b853e742addc0d8060c
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089495"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Uno o varios elementos seleccionados contienen un tipo de datos que el diseñador no admite

Uno o varios de los elementos arrastran desde **Explorador de servidores** o **Database Explorer** hasta la **Object Relational Designer** contiene un tipo de datos que no es compatible con la **O /R diseñador**, por ejemplo, [tipos definidos por el usuario CLR](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Para corregir este error

1. Cree una vista basada en la tabla deseada y que no incluya el tipo de datos no admitidos.

2. Arrastre la vista del **Explorador de servidores** o **Database Explorer** hasta el diseñador.

## <a name="see-also"></a>Vea también

- [Mensajes de Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)