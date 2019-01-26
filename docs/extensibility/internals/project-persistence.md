---
title: Persistencia del proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15b605d4beffc85c2ac5e8803d627c13dd4c7d38
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021811"
---
# <a name="project-persistence"></a>Persistencia de un proyecto
Persistencia es una consideración de diseño clave para el proyecto. La mayoría de los proyectos usan elementos de proyecto que representan los archivos; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] también es compatible con los proyectos cuyos datos están basados en archivos que no sean. Se deben conservar los archivos de propiedad del proyecto y el archivo de proyecto. El IDE indica que el proyecto para guardar en sí mismo o a un elemento de proyecto.  
  
 Plantillas de proyectos se pasan en el generador de proyectos. Las plantillas deben admitir la inicialización de todos los elementos de proyecto según los requisitos del tipo de proyecto específico. Estas plantillas más adelante pueden se guardan como archivos de proyecto y administradas por el IDE a través de la solución. Para obtener más información, consulte [crear proyecto instancias por usar generadores de proyectos](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) y [soluciones](../../extensibility/internals/solutions.md).  
  
 Elementos de proyecto pueden ser basados en archivos o no basada en archivo:  
  
-   Los elementos basados en el archivo pueden ser local o remoto. En los proyectos Web en C#, por ejemplo, las conexiones a los archivos en un sistema remoto se conservan localmente, mientras que los propios archivos se conservan en el sistema remoto.  
  
-   Elementos basados en archivos no pueden guardar elementos en un repositorio o una base de datos.  
  
## <a name="commit-models"></a>Confirmar los modelos  
 Después de decidir dónde se encuentran los elementos de proyecto, debe elegir el modelo adecuado de confirmación. Por ejemplo, en un modelo basado en archivos con los archivos locales, cada proyecto puede guardarse forma autónoma. En un modelo de repositorio, puede guardar varios elementos en una transacción. Para obtener más información, consulte [decisiones de diseño de tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md).  
  
 Para determinar las extensiones de nombre de archivo, implementan proyectos de la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfaz, que proporciona información que permita al cliente de un objeto que implemente la **Guardar como** cuadro de diálogo, es decir, para rellenar el **Guardar como tipo**  desplegable enumerar y administrar la extensión de nombre de archivo inicial.  
  
 Las llamadas IDE el `IPersistFileFormat` elementos de interfaz en el proyecto para indicar que el proyecto debe conservar su proyecto según corresponda. Por lo tanto, el objeto posee todos los aspectos de su archivo y el formato. Esto incluye el nombre del formato del objeto.  
  
 En el caso donde los elementos no son archivos, `IPersistFileFormat` sigue siendo cómo no basados en archivos se conservan los elementos. Archivos de proyecto, como los archivos .vbp para [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .vcproj o proyectos de archivos para [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proyectos, también deben conservarse.  
  
 Para guardar las acciones, el IDE examina la tabla de documentos en ejecución (RDT) y la jerarquía pasa los comandos para el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> interfaces. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> se implementa el método para determinar si se ha modificado el elemento. Si el elemento tiene, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> método se implementa para guardar el elemento modificado.  
  
 Los métodos de la `IVsPersistHierarchyItem2` interfaz se usan para determinar si un elemento puede volver a cargarse y, si el elemento puede ser, al volver a cargarlo. Además, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> método se puede implementar para que los elementos modificados se descarta sin que se va a guardar.  
  
## <a name="see-also"></a>Vea también  
 [Lista de comprobación: Creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)