---
title: Trabajar con conjuntos de datos en aplicaciones de n niveles
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c7532bed6a7d43c24d698870723d2265fc2b176f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585930"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Trabajar con conjuntos de datos en aplicaciones de n niveles

Las *aplicaciones de datos con n niveles* son aplicaciones centradas en datos que están separadas en varias capas lógicas (o *niveles*). Dicho de otro modo, una aplicación de datos con n niveles es una aplicación dividida en varios proyectos, con el correspondiente nivel de acceso a datos, nivel de lógica empresarial y nivel de presentación en cada proyecto. Para obtener más información, vea [información general sobre aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md).

Los conjuntos de datos con tipo se han mejorado de forma que los TableAdapter y las clases de conjunto de datos se puedan generar en proyectos discretos. Esto hace posible que los niveles de la aplicación se puedan separar rápidamente, así como generar aplicaciones de datos con n niveles.

La compatibilidad con n niveles en conjuntos de datasets con tipo permite el desarrollo iterativo de la arquitectura de la aplicación en un diseño de n niveles. También quita el requisito de separar manualmente el código en más de un proyecto. Comience a diseñar la capa de datos mediante el **Diseñador de DataSet**. Cuando esté listo para llevar la arquitectura de la aplicación a un diseño con n niveles, establezca la propiedad **DataSet Project** de un conjunto de datos de forma que la clase del conjunto de datos se genere en un proyecto por separado.

## <a name="reference"></a>Referencia

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>Vea también

- [Introducción a las aplicaciones de datos de n niveles](../data-tools/n-tier-data-applications-overview.md)
- [Tutorial: Creación de una aplicación de datos con n niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Agregar código a TableAdapters en aplicaciones con n niveles](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Agregar código a conjuntos de datos en aplicaciones con n niveles](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Agregar validación a un conjunto de datos con n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Separar conjuntos de datos y TableAdapters en proyectos diferentes](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Actualización jerárquica](../data-tools/hierarchical-update.md)
- [Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)
- [Aplicaciones de n niveles y remotas con LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)
