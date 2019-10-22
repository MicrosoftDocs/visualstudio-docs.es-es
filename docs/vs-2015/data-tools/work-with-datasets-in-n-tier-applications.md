---
title: Trabajar con conjuntos de valores en aplicaciones de n niveles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f7be307ec94b15871da20ace8055fc7121d5d92
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657808"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Trabajar con conjuntos de datos en aplicaciones de n niveles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las aplicaciones de datos con N niveles * son aplicaciones centradas en datos que están separadas en varias capas lógicas (o *niveles*). Dicho de otro modo, una aplicación de datos con n niveles es una aplicación dividida en varios proyectos, con el correspondiente nivel de acceso a datos, nivel de lógica empresarial y nivel de presentación en cada proyecto. Para obtener más información, vea [información general sobre aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md).

 Los conjuntos de datos con tipo se han mejorado de forma que los TableAdapter y las clases de conjunto de datos se puedan generar en proyectos discretos. Esto hace posible que los niveles de la aplicación se puedan separar rápidamente, así como generar aplicaciones de datos con n niveles.

 La compatibilidad con n niveles en conjuntos de datasets con tipo permite el desarrollo iterativo de la arquitectura de la aplicación en un diseño de n niveles. También quita el requisito de separar manualmente el código en más de un proyecto. Comience a diseñar la capa de datos mediante el Diseñador de DataSet. Cuando esté listo para llevar la arquitectura de la aplicación a un diseño con n niveles, establezca la propiedad **DataSet Project** de un conjunto de datos de forma que la clase del conjunto de datos se genere en un proyecto por separado.

## <a name="in-this-section"></a>En esta sección
 [Separar conjuntos de objetos y TableAdapters en proyectos diferentes](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md) Describe cómo trasladar la clase DataSet generada fuera del proyecto que contiene las clases TableAdapter generadas y a un nuevo proyecto.

 [Agregar código a TableAdapters en aplicaciones de n niveles](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md) Describe cómo generar una clase parcial en la que se puede agregar código para un TableAdapter con n niveles.

 [Agregar código a conjuntos de valores en aplicaciones de n niveles](../data-tools/add-code-to-datasets-in-n-tier-applications.md) Describe cómo generar una clase parcial en la que se puede agregar código para un conjunto de información de n niveles.

 [Agregar validación a un conjunto de información de n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md) Describe dónde agregar código para realizar la validación de los datos modificados.

 [Tutorial: crear una aplicación de datos de N niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md) Proporciona instrucciones paso a paso para crear un conjunto de un DataSet con tipo y separar el código TableAdapter y el conjunto de objetos en varios proyectos.

 [Tutorial: agregar validación a una aplicación de datos de N niveles](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265) Proporciona instrucciones paso a paso para agregar validación a la aplicación que se creó en el tutorial de la aplicación de datos de n niveles.

## <a name="reference"></a>Referencia
 <xref:System.Data.DataSet>

 <xref:System.Data.TypedTableBase%601>

## <a name="related-sections"></a>Secciones relacionadas

- [Introducción a las aplicaciones de datos con n capas](../data-tools/n-tier-data-applications-overview.md)
- [Actualización jerárquica](../data-tools/hierarchical-update.md)
- [Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Aplicaciones de n niveles y remotas con LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)