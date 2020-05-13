---
title: Persistencia del proyecto ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10a9cde91c0181fbfefbaa353c7c3702f4b36819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706462"
---
# <a name="project-persistence"></a>Persistencia de un proyecto
La persistencia es una consideración de diseño clave para su proyecto. La mayoría de los proyectos usan elementos de proyecto que representan archivos; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] también admite proyectos cuyos datos no están basados en archivos. Tanto los archivos propiedad del proyecto como el archivo de proyecto deben conservarse. El IDE indica al proyecto que se guarde a sí mismo o a un elemento de proyecto.

 Las plantillas para proyectos se pasan a la fábrica de proyectos. Las plantillas deben admitir la inicialización de todos los elementos de proyecto según los requisitos del tipo de proyecto específico. Estas plantillas se pueden guardar más adelante como archivos de proyecto y administrar por el IDE a través de la solución. Para obtener más información, vea [Creación de instancias](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) de proyecto mediante el uso de factorías y [soluciones](../../extensibility/internals/solutions-overview.md)de proyectos .

 Los elementos del proyecto pueden estar basados en archivos o no en archivos:

- Los elementos basados en archivos pueden ser locales o remotos. En los proyectos web en C-, por ejemplo, las conexiones a archivos en un sistema remoto persisten localmente, mientras que los propios archivos persisten en el sistema remoto.

- Los elementos no basados en archivos pueden guardar elementos en una base de datos o repositorio.

## <a name="commit-models"></a>Confirmar modelos
 Después de decidir dónde se encuentran los elementos del proyecto, debe elegir el modelo de confirmación adecuado. Por ejemplo, en un modelo basado en archivos con archivos locales, cada proyecto se puede guardar de forma autónoma. En un modelo de repositorio, puede guardar varios elementos en una transacción. Para obtener más información, vea [Decisiones](../../extensibility/internals/project-type-design-decisions.md)de diseño de tipo de proyecto .

 Para determinar las extensiones <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> de nombre de archivo, los proyectos implementan la interfaz, que proporciona información que permite al cliente de un objeto implementar el cuadro de diálogo **Guardar como,** es decir, rellenar la lista desplegable Guardar como **tipo** y administrar la extensión de nombre de archivo inicial.

 El IDE `IPersistFileFormat` llama a la interfaz en el proyecto para indicar que el proyecto debe conservar sus elementos de proyecto según corresponda. Por lo tanto, el objeto posee todos los aspectos de su archivo y formato. Esto incluye el nombre del formato del objeto.

 En el caso de que `IPersistFileFormat` los elementos no sean archivos, sigue siendo cómo se conservan los elementos no basados en archivos. Los archivos de proyecto, como [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] los archivos .vbp para proyectos o los archivos .vcproj para [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proyectos, también deben conservarse.

 Para las acciones de guardado, el IDE examina la tabla de documentos <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> ejecución (RDT) y la jerarquía pasa los comandos a las interfaces y las. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> método se implementa para determinar si el elemento se ha modificado. Si el elemento <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> tiene, el método se implementa para guardar el elemento modificado.

 Los métodos `IVsPersistHierarchyItem2` de la interfaz se utilizan para determinar si se puede volver a cargar un elemento y, si el elemento puede ser, para volver a cargarlo. Además, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> el método se puede implementar para hacer que los elementos modificados se descarten sin guardarse.

## <a name="see-also"></a>Vea también
- [Lista de comprobación: creación de nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
