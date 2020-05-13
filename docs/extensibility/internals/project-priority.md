---
title: Prioridad del proyecto ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a75c1c333d88e1bf5524281bee8b2a683ca6c98e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706417"
---
# <a name="project-priority"></a>Prioridad del proyecto
Normalmente, un elemento de proyecto es miembro de un solo proyecto de la solución. Por lo tanto, el IDE puede determinar fácilmente qué proyecto se usa para abrir el elemento. Sin embargo, si un elemento es miembro de más de un proyecto, el IDE usa un esquema de prioridad para determinar el mejor proyecto para abrir el elemento.

 La lista siguiente muestra el esquema de prioridad del proyecto:

- El IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> llama al método para cada proyecto de la solución para determinar si el documento es miembro de ese proyecto.

- Si el documento es miembro del proyecto, el proyecto responde con una prioridad que el proyecto asigna según su manejo de ese documento. Por ejemplo, un proyecto de lenguaje responde con una prioridad alta para sus archivos de origen de idioma, pero responde con una prioridad más baja para un tipo de archivo no reconocido que no se utiliza como parte de su proceso de compilación.

- Los proyectos que proporcionan editores o diseñadores personalizados específicos del proyecto para un documento también reciben una alta prioridad.

- La <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeración proporciona los valores de prioridad del documento.

- El proyecto que especifica la prioridad más alta tiene el contexto para abrir el documento. Si dos proyectos devuelven valores de prioridad iguales, se prefiere el proyecto activo. Si ningún proyecto de la solución responde que puede abrir el documento, el IDE coloca el documento en el proyecto Archivos varios. Para obtener más información, consulte [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Vea también
- [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md)
- [Apertura de editores para documentos abiertos](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
