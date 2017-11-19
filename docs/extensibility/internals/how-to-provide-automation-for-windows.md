---
title: "Cómo: proporcionar la automatización para Windows | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 945eeb8b81ecb26d43da9528db154d133c4f868c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-provide-automation-for-windows"></a>Cómo: proporcionar la automatización para Windows
Puede proporcionar la automatización para ventanas de herramientas y documentos. Al proporcionar automatización es aconsejable siempre que desea que los objetos de automatización estén disponibles en una ventana, y el entorno no proporcione un objeto de automatización listos para su uso, como lo hace con una lista de tareas.  
  
## <a name="automation-for-tool-windows"></a>Automatización de las ventanas de herramientas  
 El entorno proporciona automatización en una ventana de herramientas devolviendo un estándar <xref:EnvDTE.Window> objeto tal como se describe en el procedimiento siguiente:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Para proporcionar la automatización de las ventanas de herramientas  
  
1.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método a través del entorno con <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> como `VSFPROPID` para obtener la `Window` objeto.  
  
2.  Cuando un llamador solicita un objeto de automatización de VSPackage específico para la ventana de herramientas a través de <xref:EnvDTE.Window.Object%2A>, el entorno llama `QueryInterface` para `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, o `IDispatch` interfaces. Ambos `IExtensibleObject` y `IVsExtensibleObject` proporcionan un <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> método.  
  
3.  Cuando el entorno, a continuación, llama a la `GetAutomationObject` método pasando `NULL`, responden pasando hacer copia de su objeto específico de VSPackage.  
  
4.  Si una llamada a `QueryInterface` para `IExtensibleObject` y `IVsExtensibleObject` se produce un error, a continuación, el entorno llama `QueryInterface` para `IDispatch`.  
  
## <a name="automation-for-document-windows"></a>Automatización de las ventanas de documento  
 Un estándar <xref:EnvDTE.Document> objeto también está disponible en el entorno, aunque un editor puede tener su propia implementación de la `T:EnvDTE.Document` objeto implementando `IExtensibleObject` interfaz y responde a `GetAutomationObject`.  
  
 Además, un editor puede proporcionar un objeto de automatización específico de VSPackage, recuperado a través de la <xref:EnvDTE.Document.Object%2A> método implementando la `IVsExtensibleObject` o `IExtensibleObject` interfaces. El [muestras de VSSDK](http://aka.ms/vs2015sdksamples) contribuye a un objeto de automatización específicas del documento RTF.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>