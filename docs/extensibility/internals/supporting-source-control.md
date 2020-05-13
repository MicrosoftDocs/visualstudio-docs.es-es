---
title: Apoyo al control de código fuente ( Supporting Source Control ) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84de3120783528d209b1475477aee5087edac42b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704732"
---
# <a name="supporting-source-control"></a>Compatibilidad con control de código fuente
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]admite desprotecciones de archivos, protecciones y otras operaciones de control de código fuente para su proyecto o editor. Como cliente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] control de código fuente, está diseñado [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]para interactuar con un paquete de control de código fuente, como , que proporciona instalaciones de archivado, control de versiones y control para un conjunto de archivos definido dinámicamente.

## <a name="in-this-section"></a>En esta sección
- [Modelo para paquetes de control de código fuente](../../extensibility/internals/model-for-source-control-packages.md)

 Describe las interfaces que un tipo de proyecto debe implementar para admitir el control de código fuente.

- [Decisiones de diseño](../../extensibility/internals/source-control-design-decisions.md)

 Proporciona preguntas cuyas respuestas cambian la forma de implementar un tipo de proyecto.

- [Detalles de configuración](../../extensibility/internals/source-control-configuration-details.md)

 Describe cómo la compatibilidad con el control de código fuente cambia la implementación de un tipo de proyecto.

- [Instrucciones adicionales para proyectos y editores](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 Describe las prácticas recomendadas para los tipos de proyecto y los editores.

- [Detalles del entorno de ejecución](../../extensibility/internals/source-control-runtime-details.md)

 Describe cómo registrar un proyecto cuando un usuario lo agrega a un sistema de control de código fuente.

## <a name="reference"></a>Referencia
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>Indica al entorno o al paquete de control de código fuente que un archivo está a punto de cambiarse en la memoria o guardarse.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>Permite que los proyectos y jerarquías se registren con el control de código fuente y obtengan información sobre el estado del control de código fuente.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>Se implementa en un sistema de proyecto para proporcionar control de código fuente para los archivos de proyecto y los elementos de proyecto.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>Utilizado por los proyectos para consultar el entorno para obtener permiso para agregar, quitar o cambiar el nombre de un archivo o directorio en una solución.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>Notifica a los clientes de los cambios realizados en archivos de proyecto o directorios.

## <a name="related-sections"></a>Secciones relacionadas
- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Proporciona una visión general de los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyectos como los bloques básicos del entorno de desarrollo integrado (IDE). Se proporcionan vínculos a temas adicionales que explican cómo los proyectos controlan la creación y compilación de código.
