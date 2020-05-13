---
title: 'Cómo: Abrir editores para documentos abiertos ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d0986573ac0d53427f6490370be2bfa1c4cbe7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710914"
---
# <a name="how-to-open-editors-for-open-documents"></a>Cómo: Abrir editores para documentos abiertos
Antes de que un proyecto abra una ventana de documento, el proyecto primero debe determinar si el archivo ya está abierto en la ventana de documento para otro editor. El archivo puede estar abierto en un editor específico del proyecto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]o en uno de los editores estándar registrados con .

## <a name="open-a-project-specific-editor"></a>Abra un editor específico del proyecto
 Use el siguiente procedimiento para abrir un editor específico del proyecto para un archivo que ya está abierto.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Para abrir un editor específico del proyecto para un archivo abierto

1. Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> .

    Esta llamada devuelve punteros a la jerarquía del documento, el elemento de jerarquía y el marco de ventana, si procede.

2. Si el documento está abierto, el proyecto debe comprobar si solo existe un objeto de datos de documento o si también hay un objeto de vista de documento.

   - Si existe un objeto de vista de documento y esta vista es para una jerarquía o elemento de jerarquía diferente, el proyecto utiliza el puntero al marco de ventana de la vista para resurgir la ventana existente.

   - Si existe un objeto de vista de documento y esta vista es para el mismo elemento de jerarquía y jerarquía, el proyecto puede abrir una segunda vista si se puede asociar al objeto de datos de documento subyacente. De lo contrario, el proyecto debe usar el puntero al marco de ventana de la vista para resurgir la ventana existente.

   - Si solo existe el objeto de datos del documento, el proyecto debe determinar si puede utilizar el objeto de datos de documento para su vista. Si el objeto de datos del documento es compatible, complete los pasos descritos en [Abrir un editor específico del proyecto.](../extensibility/how-to-open-project-specific-editors.md)

     Si el objeto de datos del documento no es compatible, se debe mostrar un error al usuario que indique que el archivo está actualmente en uso. Este error solo debe mostrarse en casos transitorios, como cuando se compila un archivo al mismo tiempo que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el usuario intenta abrir el archivo mediante un editor que no sea el editor de texto principal. El editor de texto principal puede compartir el objeto de datos de documento con el compilador.

3. Si el documento no está abierto porque no hay ningún objeto de datos de documento o objeto de vista de documento, complete los pasos descritos en [Abrir un editor específico del proyecto.](../extensibility/how-to-open-project-specific-editors.md)

## <a name="open-a-standard-editor"></a>Abrir un editor estándar
 Utilice el siguiente procedimiento para abrir un editor estándar para un archivo que ya está abierto.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>Para abrir un editor estándar para un archivo abierto

1. Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

     Este método comprueba primero que el documento <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>aún no está abierto llamando a . Si el documento ya está abierto, se vuelve a aparecer su ventana del editor.

2. Si el documento no está abierto, complete los pasos descritos en [Cómo: Abrir editores estándar](../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Vea también
- [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md)
- [Cómo: Abrir editores específicos de proyectos](../extensibility/how-to-open-project-specific-editors.md)
- [Cómo: Abrir editores estándar](../extensibility/how-to-open-standard-editors.md)
