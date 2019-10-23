---
title: Proyecto de archivos varios | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c46126507ef9bb293bd0fa6771f53343ad6206f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726680"
---
# <a name="miscellaneous-files-project"></a>Proyecto de archivos varios
Cuando un usuario abre elementos de proyecto, el IDE asigna al proyecto archivos varios todos los elementos que no son miembros de ningún proyecto de una solución.

 Los proyectos desempeñan un papel importante a la hora de determinar qué editor se usa cuando un usuario abre un elemento de proyecto. Un proyecto se puede diseñar para abrir determinados archivos mediante un editor específico del proyecto o un editor estándar.

 Normalmente, un editor específico del proyecto requiere que el usuario tenga un conocimiento especial o use interfaces especiales del proyecto. Para obtener más información, consulte [Cómo: abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md).

 Un editor estándar puede abrir cualquier archivo de una extensión específica en cualquier proyecto. El usuario puede personalizar algunos editores estándar, como el editor de texto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], para los proyectos pero conserva su carácter público. Los editores estándar se crean mediante el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

 Si ningún proyecto de la solución responde que puede abrir un elemento de proyecto, el IDE proporciona un proyecto especial denominado proyecto de archivos varios que abre cualquier archivo.

 Este proyecto especial proporciona la apertura de un archivo fuera del contexto de un proyecto. Durante el procesamiento del método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>, el proyecto archivos varios siempre responde con una prioridad muy baja. Por lo tanto, el proyecto archivos varios siempre cede a cualquier proyecto de mayor prioridad que pueda abrir archivos.

 El proyecto archivos varios no requiere que el usuario lo cree explícitamente con el cuadro de diálogo **nuevo proyecto** . Además, el proyecto archivos varios no administra de forma permanente una lista de miembros del proyecto. Usa una característica opcional para grabar una lista de archivos usados más recientemente para cada usuario.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Apertura de editores específicos de proyecto](../../extensibility/how-to-open-project-specific-editors.md)
- [Apertura de editores estándar](../../extensibility/how-to-open-standard-editors.md)
- [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)