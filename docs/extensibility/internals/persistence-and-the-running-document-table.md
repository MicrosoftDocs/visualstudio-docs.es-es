---
title: Persistencia y el que se ejecuta en el documento tabla | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 51f3d2cc41c9adaf97215701ad01da2e59d245a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="persistence-and-the-running-document-table"></a>Persistencia y la tabla Document de ejecución
En el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, los proyectos son completamente responsables de administrar la persistencia de sus elementos de proyecto que llevar a cabo mediante el servicio, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Documentos son la unidad básica de persistencia en el entorno de Visual Studio. Proyectos de coordinan la apertura, guardar y cambiar el nombre de los documentos con la tabla de documento ejecución (RDT), un recurso que realiza un seguimiento del estado de todos los documentos abiertos.  
  
## <a name="managing-persistence"></a>Administración de persistencia  
 Proyectos de control de servicio de persistencia del entorno mediante la implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interfaz. Mientras el entorno pide nunca directamente un documento para conservar propio, solicita el proyecto propietario (o jerarquía) para guardar el documento. Esto hace posible para el proyecto guardar sus datos de elemento de proyecto en archivos locales, archivos remotos, una base de datos, un repositorio o cualquier otro medio.  
  
 El entorno global mantiene el RDT. El entorno mantiene las entradas para todas las ventanas abiertas y documentos en el RDT, que hace posible para que puedan reciban notificaciones especiales, como cuando se cierra una solución. Además, el RDT, es posible que el entorno realizar el seguimiento de sus nodos correspondientes en **el Explorador de soluciones**. El RDT mantiene un registro por cada objeto abierto y con persistencia, incluidos los archivos de proyecto y documentos de elemento de proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Tabla de documentos en ejecución](../../extensibility/internals/running-document-table.md)   
 [Selección y moneda en el IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)