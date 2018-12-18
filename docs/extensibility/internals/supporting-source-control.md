---
title: Compatibilidad con Control de código fuente | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9ae3590a5d02c2b3f1d4b67f724d0177f671f7d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130695"
---
# <a name="supporting-source-control"></a>Compatibilidad con Control de código fuente
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite desprotecciones del archivo, protecciones y otras operaciones de control de origen de su proyecto o el editor. Como un cliente de control de código fuente, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está diseñado para interactuar con un paquete de control de código fuente, como [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], que proporciona archivado, control de versiones y funciones de control para un conjunto de archivos definido dinámicamente.  
  
## <a name="in-this-section"></a>En esta sección  
 [Modelo para paquetes de control de código fuente](../../extensibility/internals/model-for-source-control-packages.md)  
 Describe las interfaces que debe implementar un tipo de proyecto para admitir el control de código fuente.  
  
 [Decisiones de diseño](../../extensibility/internals/source-control-design-decisions.md)  
 Proporciona preguntas cuyas respuestas cambiar cómo implementar un tipo de proyecto.  
  
 [Detalles de configuración](../../extensibility/internals/source-control-configuration-details.md)  
 Describe cómo admitir el control de código fuente cambia la implementación de un tipo de proyecto.  
  
 [Directrices adicionales para los proyectos y editores](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Analiza los procedimientos recomendados para los tipos de proyecto y editores.  
  
 [Detalles de tiempo de ejecución](../../extensibility/internals/source-control-runtime-details.md)  
 Describe cómo registrar un proyecto cuando un usuario agrega a un sistema de control de código fuente.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Indica que el entorno o el paquete de control de origen que va a modificarse en la memoria o guardar un archivo.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Permite que los proyectos y las jerarquías que se registran con el control de código fuente y obtener información sobre el estado del control de código fuente.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Se implementa en un sistema de proyecto para proporcionar control de código fuente para los archivos de proyecto y elementos de proyecto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Usar proyectos para consultar el entorno para obtener permiso para agregar, quitar o cambiar el nombre de un archivo o directorio en una solución.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Notifica a los clientes de los cambios realizados en los archivos de proyecto o directorios.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona información general de los proyectos como bloques de creación básicos de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE). Se proporcionan vínculos a temas adicionales que se explica cómo controlan los proyectos de generar y compilar código.