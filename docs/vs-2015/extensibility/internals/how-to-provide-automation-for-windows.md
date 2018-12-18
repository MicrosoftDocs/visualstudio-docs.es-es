---
title: 'Cómo: proporcionar automatización para Windows | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d1c16b0688cd5fa07fee8be0296958b23aa8c0ae
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742335"
---
# <a name="how-to-provide-automation-for-windows"></a>Cómo: proporcionar automatización para Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Puede proporcionar automatización para ventanas de herramientas y documentos. Proporcionar automatización es aconsejable cada vez que se desea disponer de los objetos de automatización en una ventana, y el entorno no proporciona un objeto de automatización listos para su uso, ya que lo hace con una lista de tareas.  
  
## <a name="automation-for-tool-windows"></a>Automatización de la herramienta Windows  
 El entorno proporciona automatización en una ventana de herramientas devolviendo un estándar <xref:EnvDTE.Window> objeto tal como se explica en el procedimiento siguiente:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Para proporcionar automatización para ventanas de herramientas  
  
1.  Llame a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método a través del entorno con <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> como `VSFPROPID` para obtener el `Window` objeto.  
  
2.  Cuando un llamador solicita un objeto de automatización específico de VSPackage de la ventana de herramientas a través de <xref:EnvDTE.Window.Object%2A>, el entorno llama a `QueryInterface` para `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, o el `IDispatch` interfaces. Ambos `IExtensibleObject` y `IVsExtensibleObject` proporcionan un <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> método.  
  
3.  Cuando el entorno, a continuación, llama a la `GetAutomationObject` método pasando `NULL`, realizar una copia de responder al pasar el objeto específico de VSPackage.  
  
4.  Si una llamada a `QueryInterface` para `IExtensibleObject` y `IVsExtensibleObject` produce un error, el entorno llama a `QueryInterface` para `IDispatch`.  
  
## <a name="automation-for-document-windows"></a>Automatización de Windows de documento  
 Un estándar <xref:EnvDTE.Document> objeto también está disponible desde el entorno, aunque un editor puede tener su propia implementación de la `T:EnvDTE.Document` objeto implementando `IExtensibleObject` interfaz y responder a `GetAutomationObject`.  
  
 Además, un editor puede proporcionar un objeto de automatización específico de VSPackage, recuperado a través de la <xref:EnvDTE.Document.Object%2A> método implementando la `IVsExtensibleObject` o `IExtensibleObject` interfaces. El [muestras de VSSDK](../../misc/vssdk-samples.md) contribuye a un objeto de automatización específicos del documento RTF.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>

