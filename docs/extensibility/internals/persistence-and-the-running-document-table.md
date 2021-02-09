---
title: Persistencia y la tabla de documentos en ejecución | Microsoft Docs
description: Obtenga información sobre cómo los proyectos coordinan la apertura, el guardado y el cambio de nombre de documento en la tabla de documentos en ejecución, que realiza un seguimiento del estado del documento en el IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6070cba3e24f16da0bf5619fc979e0d4471971c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895458"
---
# <a name="persistence-and-the-running-document-table"></a>Persistencia y tabla de documentos en ejecución
En el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, los proyectos son completamente responsables de administrar la persistencia de sus elementos de proyecto, que se realizan mediante el servicio <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Los documentos son la unidad básica de persistencia en el entorno de Visual Studio. Los proyectos coordinan la apertura, el guardado y el cambio de nombre de los documentos con la tabla de documentos en ejecución (RDT), un recurso que realiza un seguimiento del estado de todos los documentos abiertos.

## <a name="managing-persistence"></a>Administrar la persistencia
 Los proyectos controlan el servicio de persistencia del entorno implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interfaz. Aunque el entorno nunca pide directamente a un documento que se conserve, pide al proyecto (o jerarquía) propietario que guarde el documento. Esto hace posible que el proyecto guarde los datos del elemento de proyecto en archivos locales, archivos remotos, una base de datos, un repositorio u otro medio.

 El entorno global mantiene el RDT. El entorno mantiene entradas para todas las ventanas y documentos abiertos en el RDT, lo que permite que reciban notificaciones especiales, como cuando se cierra una solución. Además, el RDT permite que el entorno realice un seguimiento de sus nodos correspondientes en **Explorador de soluciones**. El RDT mantiene un registro por cada objeto de apertura y persistencia, incluidos los archivos de proyecto y los documentos de elementos de proyecto.

## <a name="see-also"></a>Vea también
- [Tabla de documentos en ejecución](../../extensibility/internals/running-document-table.md)
- [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
