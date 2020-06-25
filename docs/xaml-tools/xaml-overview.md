---
title: Información general sobre XAML
ms.date: 06/23/2020
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e14e23f9820301374bd435484ba784edf50294bb
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331948"
---
# <a name="overview-of-xaml"></a>Información general de XAML

El lenguaje XAML (XAML) es un lenguaje declarativo basado en XML. XAML se usa mayoritariamente en estos tipos de aplicaciones para crear interfaces de usuario:

- [Aplicaciones Windows Presentation Foundation (WPF)](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Aplicaciones Plataforma universal de Windows (UWP)](/windows/uwp/xaml-platform/xaml-overview)
- [Aplicaciones de Xamarin.Forms](/xamarin/xamarin-forms/xaml/)

El código XAML siguiente define un control de botón sencillo.

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

XAML también se usa para definir flujos de trabajo en las [aplicaciones de Windows WorkFlow Foundation (WF)](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml).

## <a name="xaml-code-editor"></a>Editor de código XAML

El [Editor de código XAML](xaml-code-editor.md) del IDE de Visual Studio incluye todas las herramientas que necesita para crear aplicaciones de WPF y UWP para la plataforma Windows y para Xamarin. Forms. Aunque el IDE (entorno de desarrollo integrado) de Visual Studio tiene muchas características que puede usar para desarrollar aplicaciones para otras plataformas, también tiene algunas características que son exclusivas de XAML.

## <a name="xaml-designer"></a>XAML Designer

Visual Studio y Blend para Visual Studio proporcionan una [Diseñador XAML](creating-a-ui-by-using-xaml-designer-in-visual-studio.md) que le ayuda a crear interfaces de usuario (UI) para aplicaciones de WPF, UWP y Xamarin. Forms. Puede arrastrar controles desde la ventana de Recursos o del cuadro de herramientas y establecer propiedades en la ventana Propiedades. Al hacerlo, Visual Studio y Blend para Visual Studio crear el código XAML correspondiente. Si prefiere editar directamente el código XAML, también puede hacerlo.

## <a name="whats-new"></a>Novedades

Para obtener la información más reciente, consulte los siguientes recursos:

- Las **[mejoras de las herramientas de XAML en la entrada de blog de Visual Studio 2019 versión 16,7 Preview 1](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/)**
- Entrada de blog sobre las novedades **[de las herramientas de desarrollo de XAML en Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/)**
- Las **[nuevas características de XAML en Visual Studio](https://youtu.be/yI9OyA4ZM2E)** vídeo en YouTube

## <a name="see-also"></a>Vea también

- [XAML en aplicaciones de WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML en aplicaciones de UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML en aplicaciones de Xamarin.Forms](/xamarin/xamarin-forms/xaml/)
