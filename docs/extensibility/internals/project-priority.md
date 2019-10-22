---
title: Prioridad del proyecto | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1badd483690ae22f9e314c0f9eb4ac3033d82e4a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328277"
---
# <a name="project-priority"></a>Prioridad del proyecto
Normalmente, un elemento de proyecto es un miembro de un único proyecto de la solución. Por lo tanto, el IDE puede determinar fácilmente qué proyecto se usa para abrir el elemento. Sin embargo, si un elemento es un miembro de más de un proyecto, el IDE usa un esquema de prioridad para determinar el proyecto de procedimiento para abrir el elemento.

 En la lista siguiente se muestra el esquema de prioridad del proyecto:

- Las llamadas IDE el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> método para cada proyecto de la solución para determinar si el documento es un miembro de ese proyecto.

- Si el documento es un miembro del proyecto, el proyecto responde con una prioridad que el proyecto se asigna según su propio control de ese documento. Por ejemplo, un proyecto de lenguaje responde con una prioridad alta para sus archivos de código fuente del lenguaje pero responde con una prioridad más baja para un tipo de archivo no reconocido que no se usa como parte de su proceso de compilación.

- Proyectos que ofrecen personalizados, específicas del proyecto editores o diseñadores para un documento también reciben una prioridad alta.

- El <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeración proporciona valores de prioridad de documento.

- El proyecto que especifica la prioridad más alta se proporciona el contexto para abrir el documento. Si dos proyectos devuelvan valores de la misma prioridad, se prefiere el proyecto activo. Si ningún proyecto de la solución responde que puede abrir el documento, el IDE coloca el documento en el proyecto archivos varios. Para obtener más información, consulte [proyecto archivos varios](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Vea también
- [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md)
- [Cómo: Abrir editores para documentos abiertos](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)