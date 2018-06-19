---
title: 'Cómo: abrir editores de documentos abiertos | Documentos de Microsoft'
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
ms.openlocfilehash: 621ed4436160b6f491abb34d8194c75595d9a54c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129816"
---
# <a name="how-to-open-editors-for-open-documents"></a>Cómo: abrir editores para los documentos abiertos
Antes de que un proyecto abre una ventana de documento, el proyecto en primer lugar debe determinar si el archivo ya está abierto en la ventana de documento para otro editor. El archivo puede ser cualquier abierto en un editor específico del proyecto, o uno de los editores estándares registrado en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="opening-a-project-specific-editor"></a>Abrir un Editor específico del proyecto  
 Utilice el procedimiento siguiente para abrir un editor específico del proyecto para un archivo que ya está abierto.  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Para abrir un editor específico del proyecto para un archivo abierto  
  
1.  Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>.  
  
     Esta llamada devuelve punteros a la jerarquía del documento, elemento de jerarquía y marco de ventana, si procede.  
  
2.  Si el documento está abierto, el proyecto debe comprobar para ver si existe solo un objeto de datos del documento, o si un objeto de vista de documento también está presente.  
  
    -   Si existe un objeto de vista de documento, y esta vista es para una jerarquía distinta o elemento de jerarquía, el proyecto utiliza el puntero al marco de la ventana de la vista reaparece la ventana existente.  
  
    -   Si existe un objeto de vista de documento, y esta vista está destinada a la misma jerarquía y el elemento de la jerarquía, el proyecto puede abrir una segunda vista si puede adjuntar al objeto de datos de documento subyacente. En caso contrario, el proyecto debe usar el puntero al marco de la ventana de la vista reaparece la ventana existente.  
  
    -   Si solo existe el objeto de datos del documento, el proyecto debe determinar si puede usar el objeto de datos de documento para su vista. Si el objeto de datos de documento es compatible, complete los pasos describen en [abrir un Editor específico del proyecto](../extensibility/how-to-open-project-specific-editors.md).  
  
     Si el objeto de datos del documento no es compatible, debe mostrarse un error al usuario que indica que el archivo está actualmente en uso. Este error sólo se debería mostrar en casos transitorios, como cuando se está compilando un archivo al mismo tiempo el usuario está intentando abrir el archivo mediante un editor distinto de la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor de texto del núcleo. El editor de texto básico puede compartir el objeto de datos de documento con el compilador.  
  
3.  Si el documento no está abierto, porque no hay ningún objeto de datos de documento o el objeto de vista de documento, complete los pasos de [abrir un Editor específico del proyecto](../extensibility/how-to-open-project-specific-editors.md).  
  
## <a name="opening-a-standard-editor"></a>Abrir un Editor estándar  
 Use el procedimiento siguiente para abrir un editor estándar para un archivo que ya se abra.  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>Para abrir un editor estándar para un archivo abierto  
  
1.  Llame a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
     Este método comprueba primero que el documento no está ya abierto mediante una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>. Si el documento ya está abierto, se vuelve a exponerse su ventana del editor.  
  
2.  Si el documento no está abierto, a continuación, complete los pasos de [Cómo: abrir editores estándar](../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Vea también  
 [Abrir y guardar elementos de proyecto](../extensibility/internals/opening-and-saving-project-items.md)   
 [Cómo: abrir editores específica del proyecto](../extensibility/how-to-open-project-specific-editors.md)   
 [Apertura de editores estándar](../extensibility/how-to-open-standard-editors.md)