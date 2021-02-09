---
title: 'Cómo: proporcionar automatización para Windows | Microsoft Docs'
description: Obtenga información sobre cómo proporcionar automatización para las ventanas de documentos y herramientas en Visual Studio mediante el uso de los métodos de Microsoft. VisualStudio. Shell. Interop.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- automation [Visual Studio SDK], tool windows
- tool windows, automation
ms.assetid: 512ab2a4-7987-4912-8f40-8804bf66f829
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 518a9d53b0bf03a1c57046789452ed007e6188f6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888984"
---
# <a name="how-to-provide-automation-for-windows"></a>Cómo: proporcionar automatización para Windows

Puede proporcionar automatización para las ventanas de documento y de herramientas. Es aconsejable proporcionar automatización siempre que desee que los objetos de automatización estén disponibles en una ventana de y el entorno no proporcione ya un objeto de automatización preparado, como hace con una lista de tareas.

## <a name="automation-for-tool-windows"></a>Automatización para las ventanas de herramientas

El entorno proporciona automatización en una ventana de herramientas al devolver un <xref:EnvDTE.Window> objeto estándar, como se explica en el procedimiento siguiente:

1. Llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método a través del entorno con [__VSFPROPID. VSFPROPID_ExtWindowObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ExtWindowObject>) como `VSFPROPID` parámetro para obtener el `Window` objeto.

2. Cuando un autor de llamada solicita un objeto de automatización específico de VSPackage para la ventana de herramientas a través de <xref:EnvDTE.Window.Object%2A> , el entorno de llama a `QueryInterface` `IExtensibleObject` , <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> o las `IDispatch` interfaces. `IExtensibleObject`Y `IVsExtensibleObject` proporcionan un <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject.GetAutomationObject%2A> método.

3. Cuando el entorno llama después al `GetAutomationObject` método Passing `NULL` , responde pasando el objeto específico de VSPackage.

4. Si `QueryInterface` `IExtensibleObject` `IVsExtensibleObject` se produce un error en la llamada a para y, el entorno llama a `QueryInterface` para `IDispatch` .

## <a name="automation-for-document-windows"></a>Automatización para ventanas de documento

Un <xref:EnvDTE.Document> objeto estándar también está disponible en el entorno, aunque un editor puede tener su propia implementación del objeto implementando la <xref:EnvDTE.Document> `IExtensibleObject` interfaz y respondiendo a `GetAutomationObject` .

Además, un editor puede proporcionar un objeto de automatización específico de VSPackage, recuperado a través del <xref:EnvDTE.Document.Object%2A> método, mediante la implementación de las `IVsExtensibleObject` `IExtensibleObject` interfaces o. Los [ejemplos de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) aportan un objeto de automatización específico del documento RTF.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>
