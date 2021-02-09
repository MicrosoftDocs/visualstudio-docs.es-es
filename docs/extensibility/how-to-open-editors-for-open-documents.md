---
title: 'Cómo: abrir editores para documentos abiertos | Microsoft Docs'
description: Obtenga información acerca de cómo abrir un archivo en un editor estándar o específico del proyecto. Cuando un proyecto abre una ventana de documento, debe determinar si el archivo ya está abierto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 45cd616a58f51a532883eeba37f06c4eb73bd72d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850679"
---
# <a name="how-to-open-editors-for-open-documents"></a>Cómo: abrir editores para documentos abiertos
Antes de que un proyecto abra una ventana de documento, el proyecto debe determinar primero si el archivo ya está abierto en la ventana de documento de otro editor. El archivo puede estar abierto en un editor específico del proyecto o en uno de los editores estándar registrados con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="open-a-project-specific-editor"></a>Abrir un editor específico del proyecto
 Use el procedimiento siguiente para abrir un editor específico del proyecto para un archivo que ya está abierto.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Para abrir un editor específico del proyecto para un archivo abierto

1. Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> .

    Esta llamada devuelve punteros a la jerarquía del documento, al elemento de la jerarquía y al marco de la ventana, si procede.

2. Si el documento está abierto, el proyecto debe comprobar si solo existe un objeto de datos de documento, o si también hay un objeto de vista de documento.

   - Si existe un objeto de vista de documento y esta vista es para un elemento de jerarquía o jerarquía diferente, el proyecto utiliza el puntero al marco de la ventana de la vista para repartir la ventana existente.

   - Si existe un objeto de vista de documento y esta vista es para la misma jerarquía y elemento de jerarquía, el proyecto puede abrir una segunda vista si se puede adjuntar al objeto de datos de documento subyacente. De lo contrario, el proyecto debe usar el puntero al marco de la ventana de la vista para repartir la ventana existente.

   - Si solo existe el objeto de datos del documento, el proyecto debe determinar si puede utilizar el objeto de datos del documento para su vista. Si el objeto de datos del documento es compatible, complete los pasos descritos en [abrir un editor específico del proyecto](../extensibility/how-to-open-project-specific-editors.md).

     Si el objeto de datos del documento no es compatible, se debe mostrar un error al usuario que indica que el archivo está actualmente en uso. Este error solo se debe mostrar en casos transitorios, por ejemplo, cuando se compila un archivo al mismo tiempo que el usuario intenta abrir el archivo con un editor que no sea el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editor de texto básico. El editor de texto principal puede compartir el objeto de datos del documento con el compilador.

3. Si el documento no está abierto porque no hay ningún objeto de datos de documento o objeto de vista de documento, complete los pasos descritos en [abrir un editor específico del proyecto](../extensibility/how-to-open-project-specific-editors.md).

## <a name="open-a-standard-editor"></a>Abra un editor estándar.
 Use el procedimiento siguiente para abrir un editor estándar para un archivo que ya está abierto.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>Para abrir un editor estándar para un archivo abierto

1. Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

     En primer lugar, este método comprueba que el documento aún no está abierto mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> . Si el documento ya está abierto, se vuelve a mostrar la ventana del editor.

2. Si el documento no está abierto, siga los pasos descritos en [Cómo: abrir editores estándar](../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Vea también
- [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md)
- [Cómo: abrir editores específicos del proyecto](../extensibility/how-to-open-project-specific-editors.md)
- [Cómo: abrir editores estándar](../extensibility/how-to-open-standard-editors.md)
