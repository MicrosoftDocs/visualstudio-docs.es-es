---
title: 'Cómo: Proporcionar automatización para Windows Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8716fbaa56cdb77063597fd5e07f6e469cc86a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707950"
---
# <a name="how-to-provide-automation-for-windows"></a>Cómo: Proporcionar automatización para Windows

Puede proporcionar automatización para ventanas de documentos y herramientas. Proporcionar automatización es recomendable siempre que desee que los objetos de automatización estén disponibles en una ventana y el entorno no proporcione ya un objeto de automatización listo, como lo hace con una lista de tareas.

## <a name="automation-for-tool-windows"></a>Automatización de ventanas de herramientas

El entorno proporciona automatización en una <xref:EnvDTE.Window> ventana de herramientas devolviendo un objeto estándar como se explica en el procedimiento siguiente:

1. Llame <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> al método a través del entorno con [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) `VSFPROPID` como parámetro `Window` para obtener el objeto.

2. Cuando un llamador solicita un objeto de automatización <xref:EnvDTE.Window.Object%2A>específico de `QueryInterface` `IExtensibleObject`VSPackage para la ventana de herramientas a través de , el entorno llama a , <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>, o las `IDispatch` interfaces. Ambos `IExtensibleObject` `IVsExtensibleObject` y <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> proporcionar un método.

3. Cuando el entorno, `GetAutomationObject` a `NULL`continuación, llama al método que pasa , responder pasando de vuelta el objeto específico de VSPackage.

4. Si `QueryInterface` llama `IExtensibleObject` `IVsExtensibleObject` y produce un `QueryInterface` error, el entorno llama a `IDispatch`.

## <a name="automation-for-document-windows"></a>Automatización de ventanas de documentos

Un <xref:EnvDTE.Document> objeto estándar también está disponible en el entorno, aunque <xref:EnvDTE.Document> un `IExtensibleObject` editor puede `GetAutomationObject`tener su propia implementación del objeto mediante la implementación de la interfaz y la respuesta a .

Además, un editor puede proporcionar un objeto de <xref:EnvDTE.Document.Object%2A> automatización específico `IVsExtensibleObject` de `IExtensibleObject` VSPackage, recuperado a través del método, mediante la implementación de las interfaces o. Los [ejemplos de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) aportan un objeto de automatización específico del documento RTF.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
