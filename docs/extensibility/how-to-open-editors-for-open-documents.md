---
title: 'Cómo: abrir editores para documentos abiertos | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 902c7b6dffcb47c12e150ea49694d6c759d095ad
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636845"
---
# <a name="how-to-open-editors-for-open-documents"></a>Cómo: abrir editores para documentos abiertos
Antes de que un proyecto abre una ventana de documento, el proyecto en primer lugar debe determinar si el archivo ya está abierto en la ventana de documento para otro editor. El archivo puede ser cualquier abierto en un editor específico del proyecto, o uno de los editores estándares registrado con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="open-a-project-specific-editor"></a>Abra un editor específico del proyecto  
 Utilice el procedimiento siguiente para abrir un editor específico del proyecto para un archivo que ya está abierto.  
  
### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Para abrir un editor específico del proyecto para un archivo abierto  
  
1.  Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>.  
  
     Esta llamada devuelve punteros a la jerarquía del documento, elemento de la jerarquía y el marco de ventana, si procede.  
  
2.  Si el documento está abierto, el proyecto debe comprobar para ver si existe un objeto de datos del documento, o si un objeto de vista de documento también está presente.  
  
    -   Si existe un objeto de vista de documento y esta vista es para una jerarquía distinta o elemento de la jerarquía, el proyecto usa el puntero al marco de ventana de la vista reaparece la ventana existente.  
  
    -   Si existe un objeto de vista de documento y es esta vista para la misma jerarquía y elemento de jerarquía, el proyecto puede abrir una segunda vista si se puede conectar el objeto de datos subyacente. En caso contrario, el proyecto debe usar el puntero al marco de ventana de la vista reaparece la ventana existente.  
  
    -   Si solo existe el objeto de datos, el proyecto debe determinar si puede usar el objeto de datos para su vista. Si el objeto de datos es compatible, complete los pasos describen en [abrir un editor específico del proyecto](../extensibility/how-to-open-project-specific-editors.md).  
  
     Si el objeto de datos no es compatible, debe mostrarse un error al usuario que indica que el archivo está actualmente en uso. Este error solo se debe mostrar en los casos transitorios, como cuando se compila un archivo al mismo tiempo el usuario está intentando abrir el archivo con un editor distinto el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor de texto básico. El editor de texto básico puede compartir el objeto de datos de documento con el compilador.  
  
3.  Si no está abierto el documento porque no hay ningún objeto de datos de documento o el objeto de vista de documento, complete los pasos de [abrir un editor específico del proyecto](../extensibility/how-to-open-project-specific-editors.md).  
  
## <a name="open-a-standard-editor"></a>Abra un editor estándar  
 Use el procedimiento siguiente para abrir un editor estándar para un archivo que ya se abra.  
  
### <a name="to-open-a-standard-editor-for-an-open-file"></a>Para abrir un editor estándar para un archivo abierto  
  
1.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
     Este método primero comprueba que el documento no está ya abierto mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>. Si el documento ya está abierto, a continuación, se vuelve a exponerse su ventana del editor.  
  
2.  Si el documento no está abierto, a continuación, complete los pasos de [Cómo: abrir editores estándar](../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Vea también  
 [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Cómo: abrir editores específicos del proyecto](../extensibility/how-to-open-project-specific-editors.md)   
 [Cómo: abrir editores estándar](../extensibility/how-to-open-standard-editors.md)
