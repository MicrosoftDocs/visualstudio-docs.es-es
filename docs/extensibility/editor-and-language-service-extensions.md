---
title: Extensiones de Servicio de Editor e Idioma (Editor and Language Service Extensions) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e37165dc5fe9ac010545304218e807d923b424b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712022"
---
# <a name="editor-and-language-service-extensions"></a>Editor y extensiones de servicio de lenguaje
Puede ampliar la mayoría de las características del editor de código de Visual Studio. El editor se basa en Windows Presentation Foundation (WPF) y se escribe en código administrado. Aunque este diseño difiere de los diseños de versiones anteriores de Visual Studio, proporciona la mayoría de las mismas características. Para ampliar el editor, utilice Managed Extensibility Framework (MEF).

 El SDK de Visual Studio proporciona adaptadores conocidos como *compatibilidades* para admitir VSPackages que se escribieron para versiones anteriores. Sin embargo, si tiene un VSPackage existente, se recomienda actualizarlo a la nueva tecnología para obtener un mejor rendimiento y confiabilidad.

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introducción al uso de las plantillas de elementos de Editor.|
|[Ampliar el editor y los servicios de idiomas](../extensibility/extending-the-editor-and-language-services.md)|Enlaces a documentos que introducen el diseño y las características del editor principal y muestran cómo ampliarlo.|
|[Interfaces heredadas en el editor](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)|Vínculos a documentos que explican cómo acceder al editor principal desde el código existente.|
|[Crear editores y diseñadores personalizados](../extensibility/creating-custom-editors-and-designers.md)|Vínculos a documentos que explican cómo crear editores personalizados.|
|[Extensibilidad del servicio de idiomas heredado](../extensibility/internals/legacy-language-service-extensibility.md)|Vínculos a documentos que describen cómo integrar lenguajes de programación en Visual Studio.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Presenta Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Presenta Windows Presentation Foundation (WPF).|
