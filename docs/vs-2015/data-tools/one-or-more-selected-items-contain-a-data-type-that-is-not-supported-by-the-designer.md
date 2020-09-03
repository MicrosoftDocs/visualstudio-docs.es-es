---
title: Uno o varios elementos seleccionados contienen un tipo de datos no admitido por el diseñador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4e208b697da1c25dfa2e152ad08096f61c876ebe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658049"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Uno o varios elementos seleccionados contienen un tipo de datos que el diseñador no admite
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uno o varios de los elementos arrastrados desde **Explorador de servidores** / **Explorador de bases de datos** hasta [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] contiene un tipo de datos no admitido por [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (por ejemplo, los [tipos definidos por el usuario CLR](https://msdn.microsoft.com/library/9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2)).

### <a name="to-correct-this-error"></a>Para corregir este error

1. Cree una vista basada en la tabla deseada y que no incluya el tipo de datos no admitidos.

2. Arrastre la vista desde **Explorador de servidores** / **Explorador de bases de datos** hasta el diseñador.

## <a name="see-also"></a>Consulte también
 [LINQ to SQL herramientas en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [Tutorial: crear clases de LINQ to SQL (Object Relational Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
