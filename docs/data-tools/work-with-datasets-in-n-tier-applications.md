---
title: Trabajar con conjuntos de datos en aplicaciones de n niveles
description: Aprenda a trabajar con conjuntos de información en aplicaciones de n niveles. Las aplicaciones de datos con N niveles son aplicaciones centradas en datos que están separadas en varias capas lógicas (o niveles).
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 93a221640ff7383b39bfdec73cbaa9659156e33f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858077"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Trabajar con conjuntos de datos en aplicaciones de n niveles

*Las aplicaciones de datos con N niveles* son aplicaciones centradas en datos que están separadas en varias capas lógicas (o *niveles*). Dicho de otro modo, una aplicación de datos con n niveles es una aplicación dividida en varios proyectos, con el correspondiente nivel de acceso a datos, nivel de lógica empresarial y nivel de presentación en cada proyecto. Para obtener más información, vea [información general sobre aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md).

Los conjuntos de datos con tipo se han mejorado de forma que los TableAdapter y las clases de conjunto de datos se puedan generar en proyectos discretos. Esto hace posible que los niveles de la aplicación se puedan separar rápidamente, así como generar aplicaciones de datos con n niveles.

La compatibilidad con n niveles en conjuntos de datasets con tipo permite el desarrollo iterativo de la arquitectura de la aplicación en un diseño de n niveles. También quita el requisito de separar manualmente el código en más de un proyecto. Comience a diseñar la capa de datos mediante el **Diseñador de DataSet**. Cuando esté listo para llevar la arquitectura de la aplicación a un diseño con n niveles, establezca la propiedad **DataSet Project** de un conjunto de datos de forma que la clase del conjunto de datos se genere en un proyecto por separado.

## <a name="reference"></a>Referencia

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>Vea también

- [Información general sobre las aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md)
- [Tutorial: crear una aplicación de datos de n niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Agregar código a TableAdapters en aplicaciones de n niveles](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Agregar código a conjuntos de datos en aplicaciones de n niveles](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Agregar validación a un conjunto de datos de n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Separar conjuntos de datos y TableAdapters en proyectos diferentes](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Actualización jerárquica](../data-tools/hierarchical-update.md)
- [Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)
- [Aplicaciones de N niveles y remotas con LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)
