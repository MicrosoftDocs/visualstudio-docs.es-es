---
title: 'Cómo: proporcionar automatización para Windows | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f02860b76c80a05808d4e46f315fc3616a19f94f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848856"
---
# <a name="how-to-provide-automation-for-windows"></a>Cómo: proporcionar automatización para Windows

Puede proporcionar automatización para las ventanas de documento y de herramientas. Es aconsejable proporcionar automatización siempre que desee que los objetos de automatización estén disponibles en una ventana de y el entorno no proporcione ya un objeto de automatización preparado, como hace con una lista de tareas.

## <a name="automation-for-tool-windows"></a>Automatización para las ventanas de herramientas

El entorno proporciona automatización en una ventana de herramientas devolviendo un objeto de <xref:EnvDTE.Window> estándar, como se explica en el procedimiento siguiente:

1. Llame al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> a través del entorno con [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) como `VSFPROPID` parámetro para obtener el objeto `Window`.

2. Cuando un autor de llamada solicita un objeto de automatización específico de VSPackage para la ventana de herramientas a través de <xref:EnvDTE.Window.Object%2A>, el entorno llama a `QueryInterface` para `IExtensibleObject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>o las interfaces de `IDispatch`. Tanto `IExtensibleObject` como `IVsExtensibleObject` proporcionan un método <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A>.

3. Cuando el entorno llama entonces al método `GetAutomationObject` pasando `NULL`, responde pasando el objeto específico de VSPackage.

4. Si se produce un error al llamar a `QueryInterface` para `IExtensibleObject` y `IVsExtensibleObject`, el entorno llama a `QueryInterface` para `IDispatch`.

## <a name="automation-for-document-windows"></a>Automatización para ventanas de documento

Un objeto de <xref:EnvDTE.Document> estándar también está disponible en el entorno, aunque un editor puede tener su propia implementación del objeto <xref:EnvDTE.Document> implementando `IExtensibleObject` interfaz y respondiendo a `GetAutomationObject`.

Además, un editor puede proporcionar un objeto de automatización específico de VSPackage, recuperado a través del método <xref:EnvDTE.Document.Object%2A>, mediante la implementación de las interfaces `IVsExtensibleObject` o `IExtensibleObject`. Los [ejemplos de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) aportan un objeto de automatización específico del documento RTF.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
