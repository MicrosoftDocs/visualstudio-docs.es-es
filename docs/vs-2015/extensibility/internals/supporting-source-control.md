---
title: Compatibilidad con Control de código fuente | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1166197a5c79dcb0d1ddf4018227914346a6172
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995012"
---
# <a name="supporting-source-control"></a>Compatibilidad con control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] admite las protecciones de archivos, protecciones y otras operaciones de control de origen para el proyecto o el editor. Como un cliente de control de código fuente, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] está diseñado para interactuar con un paquete de control de código fuente, como [!INCLUDE[vsvss](../../includes/vsvss-md.md)], que proporciona funciones de control para un conjunto de archivos definido dinámicamente, control de versiones y archivado.  
  
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
 Proporciona información general de los proyectos como bloques de creación básicos de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE). Se proporcionan vínculos a temas adicionales que explican cómo proyectos de control de generar y compilar código.
