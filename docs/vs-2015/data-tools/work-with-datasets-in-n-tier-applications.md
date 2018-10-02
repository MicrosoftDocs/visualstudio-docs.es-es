---
title: Trabajar con conjuntos de datos en aplicaciones de n niveles | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 61f3686488a460ef4c7091521c2165f575e76fa6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578797"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Trabajar con conjuntos de datos en aplicaciones de n niveles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [trabajar con conjuntos de datos en aplicaciones de n niveles](https://docs.microsoft.com/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
  
Las aplicaciones de datos con N niveles * son aplicaciones centradas en datos que se dividen en varias capas lógicas (o *niveles*). Dicho de otro modo, una aplicación de datos con n niveles es una aplicación dividida en varios proyectos, con el correspondiente nivel de acceso a datos, nivel de lógica empresarial y nivel de presentación en cada proyecto. Para obtener más información, consulte [Introducción a las aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md).  
  
 Los conjuntos de datos con tipo se han mejorado de forma que los TableAdapter y las clases de conjunto de datos se puedan generar en proyectos discretos. Esto hace posible que los niveles de la aplicación se puedan separar rápidamente, así como generar aplicaciones de datos con n niveles.  
  
 Compatibilidad con N niveles en conjuntos de datos con tipo permite el desarrollo iterativo de la arquitectura de aplicación para un diseño de n niveles. También quita el requisito de separar manualmente el código en más de un proyecto. Empiece a diseñar la capa de datos mediante el uso de la [crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md). Cuando esté listo para aprovechar la arquitectura de aplicación a un diseño de n niveles, establezca el **DataSet Project** propiedad de un conjunto de datos para generar la clase de conjunto de datos en un proyecto independiente.  
  
## <a name="in-this-section"></a>En esta sección  
 [Separar conjuntos de datos y TableAdapters en proyectos diferentes](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 Se explica cómo sacar la clase de conjunto de datos generada del proyecto que contiene las clases TableAdapter generadas y colocarla en un nuevo proyecto.  
  
 [Agregar código a TableAdapters en aplicaciones con n niveles](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 Se explica cómo generar una clase parcial en la que se puede agregar código relativo a un TableAdapter con n niveles.  
  
 [Agregar código a conjuntos de datos en aplicaciones con n niveles](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 Se explica cómo generar una clase parcial en la que se puede agregar código relativo a un conjunto de datos con n niveles.  
  
 [Agregar validación a un conjunto de datos con n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 Se indica dónde agregar código con el que validar datos que cambian.  
  
 [Tutorial: Crear una aplicación de datos con n niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 Contiene instrucciones paso a paso para crear un conjunto de datos con tipo y separar el código de TableAdapter y del conjunto de datos en varios proyectos.  
  
 [Tutorial: Agregar validación a una aplicación de datos con N niveles](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)  
 Proporciona instrucciones paso a paso para agregar validación a la aplicación que se creó en el tutorial de la aplicación de datos con n niveles.  
  
## <a name="reference"></a>Referencia  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Introducción a las aplicaciones de datos con n capas](../data-tools/n-tier-data-applications-overview.md)  
  
 [Actualización jerárquica](../data-tools/hierarchical-update.md)  
  
 [Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
 [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
  
 [Introducción a TableAdapter](../data-tools/tableadapter-overview.md)  
  
 [Aplicaciones de n niveles y remotas con LINQ to SQL](http://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)

