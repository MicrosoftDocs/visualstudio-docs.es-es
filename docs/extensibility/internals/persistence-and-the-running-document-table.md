---
title: Persistencia y la tabla de documentos en ejecución | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f03836e1faaac03fbd89c0b93f37a698cbdcd56a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726082"
---
# <a name="persistence-and-the-running-document-table"></a>Persistencia y tabla de documentos en ejecución
En el IDE de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], los proyectos son completamente responsables de administrar la persistencia de sus elementos de proyecto, que se realizan mediante el servicio, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Los documentos son la unidad básica de persistencia en el entorno de Visual Studio. Los proyectos coordinan la apertura, el guardado y el cambio de nombre de los documentos con la tabla de documentos en ejecución (RDT), un recurso que realiza un seguimiento del estado de todos los documentos abiertos.

## <a name="managing-persistence"></a>Administrar la persistencia
 Los proyectos controlan el servicio de persistencia del entorno implementando la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>. Aunque el entorno nunca pide directamente a un documento que se conserve, pide al proyecto (o jerarquía) propietario que guarde el documento. Esto hace posible que el proyecto guarde los datos del elemento de proyecto en archivos locales, archivos remotos, una base de datos, un repositorio u otro medio.

 El entorno global mantiene el RDT. El entorno mantiene entradas para todas las ventanas y documentos abiertos en el RDT, lo que permite que reciban notificaciones especiales, como cuando se cierra una solución. Además, el RDT permite que el entorno realice un seguimiento de sus nodos correspondientes en **Explorador de soluciones**. El RDT mantiene un registro por cada objeto de apertura y persistencia, incluidos los archivos de proyecto y los documentos de elementos de proyecto.

## <a name="see-also"></a>Vea también
- [Tabla de documentos en ejecución](../../extensibility/internals/running-document-table.md)
- [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)