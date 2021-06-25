---
title: Persistencia del proyecto | Microsoft Docs
description: Obtenga información sobre la persistencia en el diseño del proyecto, incluido el uso de IPersistFileFormat para conservar los objetos de proyecto de archivos y no basados en archivos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 17b9fc40a93a926fde5edc28e93f7751b919611c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903656"
---
# <a name="project-persistence"></a>Persistencia de un proyecto
La persistencia es una consideración de diseño clave para el proyecto. La mayoría de los proyectos usan elementos de proyecto que representan archivos; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] también admite proyectos cuyos datos no están basados en archivos. Tanto los archivos que pertenecen al proyecto como el archivo de proyecto deben conservarse. El IDE indica al proyecto que se guarde a sí mismo o a un elemento de proyecto.

 Las plantillas para los proyectos se pasan al generador de proyectos. Las plantillas deben admitir la inicialización de todos los elementos de proyecto según los requisitos del tipo de proyecto específico. Estas plantillas se pueden guardar posteriormente como archivos de proyecto y administrarse mediante el IDE a través de la solución. Para obtener más información, vea [Crear instancias de proyecto mediante generadores de proyectos](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) y [soluciones.](../../extensibility/internals/solutions-overview.md)

 Los elementos del proyecto pueden estar basados en archivos o no basados en archivos:

- Los elementos basados en archivos pueden ser locales o remotos. En los proyectos web de C#, por ejemplo, las conexiones a archivos de un sistema remoto se conservan localmente, mientras que los propios archivos se conservan en el sistema remoto.

- Los elementos no basados en archivos pueden guardar elementos en una base de datos o repositorio.

## <a name="commit-models"></a>Confirmar modelos
 Después de decidir dónde se encuentran los elementos del proyecto, debe elegir el modelo de confirmación adecuado. Por ejemplo, en un modelo basado en archivos con archivos locales, cada proyecto se puede guardar de forma autónoma. En un modelo de repositorio, puede guardar varios elementos en una transacción. Para obtener más información, vea [Project Type Design Decisions](../../extensibility/internals/project-type-design-decisions.md).

 Para determinar las extensiones de nombre de archivo, los proyectos implementan la interfaz , que proporciona información que permite al cliente de un objeto implementar el cuadro de diálogo Guardar como , es decir, rellenar la lista desplegable Guardar como tipo y administrar la extensión de nombre de archivo <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> inicial.  

 El IDE llama a la interfaz del proyecto para indicar que el `IPersistFileFormat` proyecto debe conservar sus elementos de proyecto según corresponda. Por lo tanto, el objeto posee todos los aspectos de su archivo y formato. Esto incluye el nombre del formato del objeto.

 En el caso de que los elementos no sean archivos, sigue siendo el modo en que se conservan los elementos no basados `IPersistFileFormat` en archivos. Los archivos de proyecto, como los archivos .vbp para los proyectos o los archivos .vcproj para los [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] proyectos, también deben conservarse.

 Para las acciones de guardado, el IDE examina la tabla de documentos (RDT) en ejecución y la jerarquía pasa los comandos a las <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> interfaces y . El <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> método se implementa para determinar si se ha modificado el elemento. Si el elemento tiene , <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> el método se implementa para guardar el elemento modificado.

 Los métodos de la interfaz se usan para determinar si un elemento se puede volver a cargar y, si puede `IVsPersistHierarchyItem2` serlo, para volver a cargarlo. Además, el método se puede implementar para que los elementos modificados <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> se descarten sin guardarse.

## <a name="see-also"></a>Consulta también
- [Lista de comprobación: Creación de nuevos tipos de proyectos](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
