---
title: Información general sobre XAML
ms.date: 07/31/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a9b04012e2f0b046b3fd31058c9838740e833281
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2019
ms.locfileid: "68823921"
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

## <a name="xaml-designer"></a>XAML Designer

Visual Studio y Blend para Visual Studio proporciona un Diseñador XAML que lo ayuda a crear interfaces de usuario (UI) para aplicaciones de WPF, UWP y Xamarin.Forms. Puede arrastrar controles desde la ventana de Recursos o del cuadro de herramientas y establecer propiedades en la ventana Propiedades. Cuando lleve a cabo estas acciones, Visual Studio y Blend para Visual Studio crean el código XAML correspondiente. Si prefiere editar directamente el código XAML, también puede hacerlo.

En los artículos de este conjunto de documentación se describe el Diseñador XAML en Visual Studio y Blend para Visual Studio.

## <a name="see-also"></a>Vea también

- [XAML en aplicaciones de WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML en aplicaciones de UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML en aplicaciones de Xamarin.Forms](/xamarin/xamarin-forms/xaml/)