---
title: Proyecto de Archivos Varios (Varios Archivos) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95cc1312fb7b381e1e20df834698480295fadcc8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707097"
---
# <a name="miscellaneous-files-project"></a>Proyecto de archivos varios
Cuando un usuario abre elementos de proyecto, el IDE asigna al proyecto Varios archivos cualquier elemento que no sea miembro de ningún proyecto de una solución.

 Los proyectos desempeñan un papel importante a la hora de determinar qué editor se utiliza cuando un usuario abre un elemento de proyecto. Un proyecto se puede diseñar para abrir determinados archivos mediante un editor específico del proyecto o un editor estándar.

 Un editor específico del proyecto normalmente requiere que el usuario tenga conocimientos especiales o use interfaces especiales del proyecto. Para obtener más información, consulte [Cómo: Abrir editores específicos de proyecto](../../extensibility/how-to-open-project-specific-editors.md).

 Un editor estándar puede abrir cualquier archivo de una extensión específica en cualquier proyecto. El usuario puede personalizar algunos editores [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] estándar, como el editor de texto, para proyectos, pero aún conservan su carácter público. Los editores estándar se <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> crean mediante el método.

 Si ningún proyecto de la solución responde que puede abrir un elemento de proyecto, el IDE proporciona un proyecto especial denominado proyecto de archivos varios que abre cualquier archivo.

 Este proyecto especial prevé la apertura de un archivo fuera del contexto de un proyecto. Durante el procesamiento <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> del método, el proyecto Archivos varios siempre responde con una prioridad muy baja. Por lo tanto, el proyecto Archivos varios siempre cede a cualquier proyecto de mayor prioridad que pueda abrir archivos.

 El proyecto Archivos varios no requiere que el usuario lo cree explícitamente con el cuadro de diálogo **Nuevo proyecto.** Además, el proyecto Archivos varios no administra permanentemente una lista de miembros del proyecto. Utiliza una característica opcional para registrar una lista de los archivos usados más recientemente para cada usuario.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [Apertura de editores específicos de proyecto](../../extensibility/how-to-open-project-specific-editors.md)
- [Apertura de editores estándar](../../extensibility/how-to-open-standard-editors.md)
- [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
