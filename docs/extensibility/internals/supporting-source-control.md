---
title: Compatibilidad con Control de código fuente | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 523c7de972958eff9224896d3a59543163eb7b9e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936820"
---
# <a name="supporting-source-control"></a>Compatibilidad con control de código fuente
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite las protecciones de archivos, protecciones y otras operaciones de control de origen para el proyecto o el editor. Como un cliente de control de código fuente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está diseñado para interactuar con un paquete de control de código fuente, como [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], que proporciona funciones de control para un conjunto de archivos definido dinámicamente, control de versiones y archivado.  
  
## <a name="in-this-section"></a>En esta sección  
 [Modelo para paquetes de control de código fuente](../../extensibility/internals/model-for-source-control-packages.md)  
 Describe las interfaces que debe implementar un tipo de proyecto para admitir el control de código fuente.  
  
 [Decisiones de diseño](../../extensibility/internals/source-control-design-decisions.md)  
 Proporciona preguntas cuyas respuestas cambiar cómo implementar un tipo de proyecto.  
  
 [Detalles de configuración](../../extensibility/internals/source-control-configuration-details.md)  
 Describe cómo admitir el control de código fuente cambia la implementación de un tipo de proyecto.  
  
 [Instrucciones adicionales para proyectos y editores](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Describe los procedimientos recomendados para tipos de proyectos y editores.  
  
 [Detalles del entorno de ejecución](../../extensibility/internals/source-control-runtime-details.md)  
 Describe cómo registrar un proyecto cuando un usuario agrega a un sistema de control de código fuente.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Indica que el entorno o el paquete de control de código fuente que va a cambiarse en la memoria o guardar un archivo.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Permite a los proyectos y las jerarquías que se registran en el control de código fuente y obtener información sobre el estado de control de código fuente.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Se implementa en un sistema de proyectos para proporcionar control de código fuente para los archivos de proyecto y elementos de proyecto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Se usan los proyectos para consultar el entorno para obtener permiso para agregar, quitar o cambiar el nombre de un archivo o directorio en una solución.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Notifica a los clientes los cambios realizados en el proyecto archivos o directorios.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona información general de los proyectos como bloques de creación básicos de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE). Se proporcionan vínculos a temas adicionales que explican cómo proyectos de control de generar y compilar código.