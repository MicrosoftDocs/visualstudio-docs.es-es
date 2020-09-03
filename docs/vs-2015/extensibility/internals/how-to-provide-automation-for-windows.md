---
title: 'Cómo: proporcionar automatización para Windows | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ea7b79df4e7f3748ec2bc7f5e57c6ecb7dfca5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191848"
---
# <a name="how-to-provide-automation-for-windows"></a>Provisión de automatización para Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Puede proporcionar automatización para las ventanas de documento y de herramientas. Es aconsejable proporcionar automatización siempre que desee que los objetos de automatización estén disponibles en una ventana de y el entorno no proporcione ya un objeto de automatización preparado, como hace con una lista de tareas.  
  
## <a name="automation-for-tool-windows"></a>Automatización para las ventanas de herramientas  
 El entorno proporciona automatización en una ventana de herramientas al devolver un <xref:EnvDTE.Window> objeto estándar, como se explica en el procedimiento siguiente:  
  
#### <a name="to-provide-automation-for-tool-windows"></a>Para proporcionar automatización para las ventanas de herramientas  
  
1. Llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método a través del entorno con <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> como `VSFPROPID` parámetro para obtener el `Window` objeto.  
  
2. Cuando un autor de llamada solicita un objeto de automatización específico de VSPackage para la ventana de herramientas a través de <xref:EnvDTE.Window.Object%2A> , el entorno de llama a `QueryInterface` `IExtensibleObject` , <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> o las `IDispatch` interfaces. `IExtensibleObject`Y `IVsExtensibleObject` proporcionan un <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> método.  
  
3. Cuando el entorno llama después al `GetAutomationObject` método Passing `NULL` , responde pasando el objeto específico de VSPackage.  
  
4. Si `QueryInterface` `IExtensibleObject` `IVsExtensibleObject` se produce un error en la llamada a para y, el entorno llama a `QueryInterface` para `IDispatch` .  
  
## <a name="automation-for-document-windows"></a>Automatización para ventanas de documento  
 Un <xref:EnvDTE.Document> objeto estándar también está disponible en el entorno, aunque un editor puede tener su propia implementación del objeto implementando la `T:EnvDTE.Document` `IExtensibleObject` interfaz y respondiendo a `GetAutomationObject` .  
  
 Además, un editor puede proporcionar un objeto de automatización específico de VSPackage, recuperado a través del <xref:EnvDTE.Document.Object%2A> método, mediante la implementación de las `IVsExtensibleObject` `IExtensibleObject` interfaces o. Los [ejemplos de VSSDK](../../misc/vssdk-samples.md) aportan un objeto de automatización específico del documento RTF.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
