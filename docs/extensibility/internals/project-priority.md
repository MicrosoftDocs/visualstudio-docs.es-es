---
title: Prioridad del proyecto | Microsoft Docs
description: Obtenga información sobre el esquema de prioridad que Visual Studio IDE determina el mejor proyecto para abrir un elemento si el elemento es miembro de más de un proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ac0556e63b25f0f2a0df399cb23d5e2e9473008
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899646"
---
# <a name="project-priority"></a>Prioridad del proyecto
Normalmente, un elemento de proyecto es miembro de un solo proyecto de la solución. Por lo tanto, el IDE puede determinar fácilmente qué proyecto se usa para abrir el elemento. Sin embargo, si un elemento es miembro de más de un proyecto, el IDE usa un esquema de prioridad para determinar el mejor proyecto para abrir el elemento.

 En la lista siguiente se muestra el esquema de prioridad del proyecto:

- El IDE llama al método para cada proyecto de la solución para determinar si <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> el documento es miembro de ese proyecto.

- Si el documento es miembro del proyecto, el proyecto responde con una prioridad que el proyecto asigna según su control de ese documento. Por ejemplo, un proyecto de lenguaje responde con una prioridad alta para sus archivos de origen de lenguaje, pero responde con una prioridad menor para un tipo de archivo no reconocido que no se usa como parte de su proceso de compilación.

- Los proyectos que proporcionan editores o diseñadores personalizados específicos del proyecto para un documento también reciben una prioridad alta.

- La <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumeración proporciona los valores de prioridad del documento.

- El proyecto que especifica la prioridad más alta tiene el contexto para abrir el documento. Si dos proyectos devuelven valores de prioridad iguales, se prefiere el proyecto activo. Si ningún proyecto de la solución responde que pueda abrir el documento, el IDE coloca el documento en el proyecto Archivos varios. Para obtener más información, vea [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Consulta también
- [Proyecto de archivos varios](../../extensibility/internals/miscellaneous-files-project.md)
- [Apertura de editores para documentos abiertos](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
