---
title: Compatibilidad con el control de código fuente | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156077"
---
# <a name="supporting-source-control"></a>Compatibilidad con control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] admite desprotecciones de archivos, protecciones y otras operaciones de control de código fuente para el proyecto o el editor. Como cliente de control de código fuente, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] está diseñado para interactuar con un paquete de control de código fuente, como [!INCLUDE[vsvss](../../includes/vsvss-md.md)] , que proporciona funciones de archivado, control de versiones y control para un conjunto de archivos definidos dinámicamente.  
  
## <a name="in-this-section"></a>En esta sección  
 [Modelo para paquetes de control de código fuente](../../extensibility/internals/model-for-source-control-packages.md)  
 Describe las interfaces que un tipo de proyecto debe implementar para admitir el control de código fuente.  
  
 [Decisiones de diseño](../../extensibility/internals/source-control-design-decisions.md)  
 Proporciona preguntas cuyas respuestas cambian cómo se implementa un tipo de proyecto.  
  
 [Detalles de configuración](../../extensibility/internals/source-control-configuration-details.md)  
 Describe cómo el control de código fuente compatible cambia la implementación de un tipo de proyecto.  
  
 [Instrucciones adicionales para proyectos y editores](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Describe los procedimientos recomendados para los tipos de proyecto y los editores.  
  
 [Detalles del entorno de ejecución](../../extensibility/internals/source-control-runtime-details.md)  
 Describe cómo registrar un proyecto cuando un usuario lo agrega a un sistema de control de código fuente.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Indica al entorno o al paquete de control de código fuente que un archivo se va a cambiar en memoria o guardar.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Permite a los proyectos y las jerarquías registrarse con el control de código fuente y obtener información sobre el estado del control de código fuente.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Implementado en un sistema de proyectos para proporcionar control de código fuente para los archivos de proyecto y los elementos de proyecto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Lo usan los proyectos para consultar el entorno para ver si se tiene permiso para agregar, quitar o cambiar el nombre de un archivo o un directorio en una solución.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Notifica a los clientes los cambios realizados en los archivos o directorios del proyecto.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona información general sobre los proyectos como los bloques de creación básicos del [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entorno de desarrollo integrado (IDE). Se proporcionan vínculos a temas adicionales que explican cómo los proyectos controlan la compilación y compilación de código.
