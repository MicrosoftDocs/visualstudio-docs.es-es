---
title: Información general sobre XAML
description: Obtenga información básica sobre XAML, el editor de código de XAML y las herramientas de Diseñador XAML en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/23/2020
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 6f315573b24989e6ad3a3d451de372430b72f70f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931204"
---
# <a name="overview-of-xaml"></a>Información general de XAML

El lenguaje XAML (XAML) es un lenguaje declarativo basado en XML. XAML se usa mayoritariamente en estos tipos de aplicaciones para crear interfaces de usuario:

- [Aplicaciones de Windows Presentation Foundation (WPF)](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Aplicaciones de la Plataforma universal de Windows (UWP)](/windows/uwp/xaml-platform/xaml-overview)
- [Aplicaciones de Xamarin.Forms](/xamarin/xamarin-forms/xaml/)

El código XAML siguiente define un control de botón sencillo.

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

XAML también se usa para definir flujos de trabajo en las [aplicaciones de Windows WorkFlow Foundation (WF)](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml).

## <a name="xaml-code-editor"></a>Editor de código XAML

En el [editor de código XAML](xaml-code-editor.md) del IDE de Visual Studio se incluyen todas las herramientas que necesita para crear aplicaciones WPF y para UWP para la plataforma Windows y Xamarin.Forms. Aunque el IDE (Entorno de desarrollo integrado) de Visual Studio tiene muchas características que puede usar para desarrollar aplicaciones para otras plataformas, también tiene algunas que son exclusivas de XAML.

## <a name="xaml-designer"></a>XAML Designer

Visual Studio y Blend para Visual Studio proporcionan un [Diseñador XAML](creating-a-ui-by-using-xaml-designer-in-visual-studio.md) que facilita la creación de interfaces de usuario (IU) para aplicaciones WPF, para UWP y Xamarin.Forms. Puede arrastrar controles desde la ventana de Recursos o del cuadro de herramientas y establecer propiedades en la ventana Propiedades. Cuando lo haga, Visual Studio y Blend para Visual Studio crean el código XAML correspondiente. Si prefiere editar directamente el código XAML, también puede hacerlo.

## <a name="whats-new"></a>Novedades

Consulte los recursos siguientes para obtener la información más reciente:

- La entrada de blog **[Mejoras en las herramientas XAML en Visual Studio 2019 versión 16.7 Preview 1](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/)**
- La entrada de blog **[Novedades en las herramientas de desarrollo de XAML en Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/)**
- El vídeo **[Nuevas características de XAML en Visual Studio](https://youtu.be/yI9OyA4ZM2E)** en YouTube

## <a name="see-also"></a>Vea también

- [XAML en aplicaciones de WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML en aplicaciones de UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML en aplicaciones de Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
