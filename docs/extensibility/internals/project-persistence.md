---
title: Persistencia del proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7bb782b79c00576a431c8f4453ddf020606aaf5a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="project-persistence"></a>Persistencia de un proyecto
Persistencia es una consideración de diseño clave para el proyecto. Mayoría de los proyectos usa elementos de proyecto que representan archivos; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] también admite proyectos cuyos datos están no basados en archivos. Se deben conservar tanto los archivos que pertenecen al proyecto y el archivo de proyecto. El IDE indica el proyecto para guardar consigo mismo ni con un elemento de proyecto.  
  
 Plantillas para proyectos se pasan a la fábrica de proyecto. Las plantillas deben admitir la inicialización de todos los elementos de proyecto según los requisitos del tipo de proyecto específico. Estas plantillas más adelante se guardan como archivos de proyecto y administradas por el IDE a través de la solución. Para obtener más información, consulte [crear proyecto instancias por usar generadores de proyectos](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) y [soluciones](../../extensibility/internals/solutions.md).  
  
 Elementos de proyecto pueden ser basados en archivos o no basada en archivos:  
  
-   Elementos basados en archivos pueden ser locales o remotos. En los proyectos Web en C#, por ejemplo, las conexiones a los archivos en un sistema remoto se conservan localmente, mientras que los archivos se conservan en el sistema remoto.  
  
-   Elementos basados en archivos no pueden guardar elementos en una base de datos o en el repositorio.  
  
## <a name="commit-models"></a>Confirmar modelos  
 Después de decidir dónde se encuentran los elementos de proyecto, debe elegir el modelo adecuado de confirmación. Por ejemplo, en un modelo basado en archivos con archivos locales, cada proyecto puede guardarse forma autónoma. En un modelo de repositorio, puede guardar varios elementos en una transacción. Para obtener más información, consulte [decisiones de diseño del tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md).  
  
 Para determinar las extensiones de nombre de archivo, implementan proyectos de la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfaz, que proporciona información que permita al cliente de un objeto que implemente la **Guardar como** cuadro de diálogo, es decir, en blanco para igualar la **Guardar como tipo**  desplegable enumerar y administrar la extensión de nombre de archivo inicial.  
  
 Las llamadas IDE el `IPersistFileFormat` elementos de interfaz en el proyecto para indicar que el proyecto debe conservar su proyecto según corresponda. Por lo tanto, el objeto es el propietario de todos los aspectos de su archivo y el formato. Esto incluye el nombre del formato del objeto.  
  
 En el caso donde los elementos no son archivos, `IPersistFileFormat` sigue siendo cómo no basado en archivos se conservan los elementos. Archivos de proyecto, como los archivos .vbp para [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .vcproj o los proyectos de archivos para [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proyectos, también debe conservarse.  
  
 Para guardar las acciones, el IDE examina la tabla document ejecución (RDT) y la jerarquía pasa los comandos para la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> interfaces. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> se implementa el método para determinar si se ha modificado el elemento. Si el elemento tiene, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> método se implementa para guardar el elemento modificado.  
  
 Los métodos de la `IVsPersistHierarchyItem2` interfaz se usan para determinar si puede volver a cargar un elemento y, si el elemento puede ser a cargarlo. Además, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> método se puede implementar para que los elementos modificados se descarta sin que se va a guardar.  
  
## <a name="see-also"></a>Vea también  
 [Lista de comprobación: Creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)