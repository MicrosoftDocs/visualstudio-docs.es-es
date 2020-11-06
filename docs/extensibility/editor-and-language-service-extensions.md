---
title: Extensiones del editor y del servicio de lenguaje | Microsoft Docs
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
ms.openlocfilehash: 78d85cd3651f8769104a61586bea1468e1c21cd2
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414080"
---
# <a name="editor-and-language-service-extensions"></a>Extensiones del editor y del servicio de lenguaje
Puede extender la mayoría de las características del editor de código de Visual Studio. El editor se basa en el Windows Presentation Foundation (WPF) y se escribe en código administrado. Aunque este diseño difiere de los diseños de versiones anteriores de Visual Studio, proporciona la mayoría de las mismas características. Para extender el editor, use el Managed Extensibility Framework (MEF).

 El SDK de Visual Studio proporciona adaptadores denominados *correcciones de compatibilidad (Shim* ) para admitir VSPackages que se escribieron para versiones anteriores. No obstante, si tiene un VSPackage existente, se recomienda que lo actualice a la nueva tecnología para obtener un mejor rendimiento y confiabilidad.

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introducción al uso de las plantillas de elementos del editor.|
|[Extender el editor y los servicios de lenguaje](../extensibility/extending-the-editor-and-language-services.md)|Vínculos a documentos que presentan el diseño y las características del editor básico y muestran cómo extenderlo.|
|[Interfaces heredadas en el editor](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015)|Vínculos a documentos que explican cómo tener acceso al editor principal desde el código existente.|
|[Crear editores y diseñadores personalizados](../extensibility/creating-custom-editors-and-designers.md)|Vínculos a documentos que explican cómo crear editores personalizados.|
|[Extensibilidad del servicio de lenguaje heredado](../extensibility/internals/legacy-language-service-extensibility.md)|Vínculos a documentos que describen cómo integrar los lenguajes de programación en Visual Studio.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Presenta el Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Presenta el Windows Presentation Foundation (WPF).|