---
title: Trabajar con conjuntos de datos en aplicaciones de n niveles | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 85062fe6ea82a73fbc2d64e1d1ce9136d16831cf
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Trabajar con conjuntos de datos en aplicaciones de n niveles
*Aplicaciones de datos con N niveles* son aplicaciones centradas en datos que están separadas en varias capas lógicas (o *niveles*). Dicho de otro modo, una aplicación de datos con n niveles es una aplicación dividida en varios proyectos, con el correspondiente nivel de acceso a datos, nivel de lógica empresarial y nivel de presentación en cada proyecto. Para obtener más información, consulte [Introducción a las aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md).  
  
Los conjuntos de datos con tipo se han mejorado de forma que los TableAdapter y las clases de conjunto de datos se puedan generar en proyectos discretos. Esto hace posible que los niveles de la aplicación se puedan separar rápidamente, así como generar aplicaciones de datos con n niveles.  
  
Compatibilidad con N niveles en conjuntos de datos con tipo permite el desarrollo iterativo de la arquitectura de la aplicación a un diseño con n niveles. También quita el requisito de separar el código en más de un proyecto manualmente. Empiece diseñando la capa de datos mediante el uso de la **Diseñador de Dataset**. Cuando esté listo para realizar la arquitectura de la aplicación a un diseño con n niveles, establezca el **DataSet Project** propiedad de un conjunto de datos para generar la clase de conjunto de datos en un proyecto independiente.  
  
## <a name="reference"></a>Referencia  
<xref:System.Data.DataSet>  
<xref:System.Data.TypedTableBase%601>  
  
## <a name="see-also"></a>Vea también
[Introducción a las aplicaciones de datos con n capas](../data-tools/n-tier-data-applications-overview.md)  
[Tutorial: Crear una aplicación de datos con n niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
[Agregar código a TableAdapters en aplicaciones con n niveles](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
[Agregar código a conjuntos de datos en aplicaciones con n niveles](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
[Agregar validación a un conjunto de datos con n niveles](../data-tools/add-validation-to-an-n-tier-dataset.md)  
[Separar conjuntos de datos y TableAdapters en proyectos diferentes](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
[Actualización jerárquica](../data-tools/hierarchical-update.md)  
[Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
[Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
[Crear y configurar los TableAdapters](../data-tools/create-and-configure-tableadapters.md)  
[N niveles y las aplicaciones remotas con LINQ to SQL](http://msdn.microsoft.com/Library/854a1cdd-53cb-45f5-83ca-63962a9b3598)