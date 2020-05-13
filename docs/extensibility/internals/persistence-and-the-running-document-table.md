---
title: Persistencia y la tabla de documentos en ejecución ( Running Document Microsoft Docs
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba698f20b83d1a7af42aeca046aa2a8c943838ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706718"
---
# <a name="persistence-and-the-running-document-table"></a>Persistencia y tabla de documentos en ejecución
En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el IDE, los proyectos son completamente responsables de administrar la persistencia de sus elementos de proyecto, que realizan mediante el servicio, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Los documentos son la unidad básica de persistencia en el entorno de Visual Studio. Los proyectos coordinan la apertura, el guardado y el cambio de nombre de los documentos con la tabla de documentos en ejecución (RDT), un recurso que realiza un seguimiento del estado de todos los documentos abiertos.

## <a name="managing-persistence"></a>Gestión de la persistencia
 Los proyectos controlan el servicio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> persistencia del entorno mediante la implementación de la interfaz. Aunque el entorno nunca pide directamente que un documento persista, pide al proyecto propietario (o jerarquía) que guarde el documento. Esto permite que el proyecto guarde los datos de sus elementos de proyecto en archivos locales, archivos remotos, una base de datos, un repositorio u otro medio.

 El entorno global mantiene el RDT. El entorno mantiene entradas para todas las ventanas y documentos abiertos en el RDT, lo que les permite recibir notificaciones especiales, como cuando se cierra una solución. Además, el RDT permite que el entorno realice un seguimiento de sus nodos correspondientes en el **Explorador**de soluciones. El RDT mantiene un registro por objeto abierto y persistente, incluidos los archivos de proyecto y los documentos de elemento de proyecto.

## <a name="see-also"></a>Vea también
- [Tabla de documentos en ejecución](../../extensibility/internals/running-document-table.md)
- [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
