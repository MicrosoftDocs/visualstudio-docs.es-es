---
title: Persistencia del proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a95c919de9b87ed1782cbdcb029efbf191958f5a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725465"
---
# <a name="project-persistence"></a>Persistencia de un proyecto
La persistencia es una consideración de diseño clave para el proyecto. La mayoría de los proyectos utilizan elementos de proyecto que representan archivos;  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] también admite proyectos cuyos datos no estén basados en archivos. Los archivos que pertenecen al proyecto y el archivo del proyecto deben ser persistentes. El IDE indica al proyecto que se guarde o un elemento de proyecto.

 Las plantillas para los proyectos se pasan al generador de proyectos. Las plantillas deben admitir la inicialización de todos los elementos de proyecto según los requisitos del tipo de proyecto específico. Posteriormente, estas plantillas se pueden guardar como archivos de proyecto y las administra el IDE a través de la solución. Para obtener más información, vea [crear instancias de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) mediante el uso de [soluciones](../../extensibility/internals/solutions-overview.md)y generadores de proyectos.

 Los elementos de proyecto pueden estar basados en archivos o no basados en archivos:

- Los elementos basados en archivos pueden ser locales o remotos. En los proyectos Web C#de, por ejemplo, las conexiones a los archivos de un sistema remoto se conservan de forma local, mientras que los propios archivos se conservan en el sistema remoto.

- Los elementos no basados en archivos pueden guardar elementos en una base de datos o en un repositorio.

## <a name="commit-models"></a>Modelos de confirmación
 Después de decidir dónde se encuentran los elementos de proyecto, debe elegir el modelo de confirmación adecuado. Por ejemplo, en un modelo basado en archivos con archivos locales, cada proyecto se puede guardar de forma autónoma. En un modelo de repositorio, puede guardar varios elementos en una transacción. Para obtener más información, vea [decisiones de diseño de tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md).

 Para determinar las extensiones de nombre de archivo, los proyectos implementan la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>, que proporciona información que permite al cliente de un objeto implementar el cuadro de diálogo **Guardar como** , es decir, para rellenar la lista desplegable **Guardar como tipo** y administrar el extensión de nombre de archivo inicial.

 El IDE llama a la interfaz `IPersistFileFormat` del proyecto para indicar que el proyecto debe conservar sus elementos de proyecto según corresponda. Por lo tanto, el objeto posee todos los aspectos de su archivo y formato. Esto incluye el nombre del formato del objeto.

 En el caso de que los elementos no sean archivos, `IPersistFileFormat` sigue siendo el modo en que se conservan los elementos no basados en archivos. Los archivos de proyecto, como los archivos. vbp para proyectos de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o archivos. vcproj para proyectos de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], también deben ser persistentes.

 En el caso de las acciones de guardado, el IDE examina la tabla de documentos en ejecución (RDT) y la jerarquía pasa los comandos a las interfaces <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>. El método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> se implementa para determinar si se ha modificado el elemento. Si el elemento tiene, se implementa el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> para guardar el elemento modificado.

 Los métodos de la interfaz `IVsPersistHierarchyItem2` se usan para determinar si un elemento se puede volver a cargar y, si el elemento puede ser, para volver a cargarlo. Además, se puede implementar el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> para que los elementos modificados se descarten sin guardarse.

## <a name="see-also"></a>Vea también
- [Lista de comprobación: creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)