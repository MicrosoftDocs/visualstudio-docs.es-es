---
title: 'Cómo: instalar un visualizador | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b7dfd28d70b80fd2d0f854b7db3550862b32814
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404376"
---
# <a name="how-to-install-a-visualizer"></a>Cómo: Instalar un visualizador
Después de crear un visualizador, hay que instalarlo para que esté disponible en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalar un visualizador es un proceso sencillo.

> [!NOTE]
> En las aplicaciones para UWP, solo se admiten los visualizadores estándar de texto, HTML, XML y JSON. No se admiten los visualizadores personalizados (creados por el usuario).

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Para instalar un visualizador para Visual Studio 2019
  
1. Busque el archivo DLL que contiene el visualizador que compiló.

2. Copie el archivo dll [del lado depurador](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (y los archivos dll de los que depende) en cualquiera de las siguientes ubicaciones:

    - `\Common7\Packages\Debugger\Visualizers` *VisualStudioInstallPath*

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Copie la dll del [lado depurado](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) en cualquiera de las siguientes ubicaciones:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\` *VisualStudioVersion* `\Visualizers\` *Framework*

    donde *Framework* es:
    - `net2.0` para depuraciones que ejecutan el tiempo de ejecución de `.NET Framework`.
    - `netstandard2.0` para depurar a través de un tiempo de ejecución que admite `netstandard 2.0` (`.NET Framework v4.6.1+` o `.NET Core 2.0+`).
    - `netcoreapp` para depuraciones que ejecutan el tiempo de ejecución de `.NET Core`. (admite `.NET Core 2.0+`)

4. Reinicie la sesión de depuración.

> [!NOTE]
> El procedimiento es diferente en Visual Studio 2017 y versiones anteriores. Vea la [versión anterior](how-to-install-a-visualizer.md?view=vs-2017) de este artículo.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Para instalar un visualizador para Visual Studio 2017 y versiones anteriores

> [!IMPORTANT]
> Solo se admiten .NET Framework visualizadores en Visual Studio 2017 y versiones anteriores.

1. Busque el archivo DLL que contiene el visualizador que ha compilado.

2. Copie el archivo DLL a una de las siguientes ubicaciones:

    - `\Common7\Packages\Debugger\Visualizers` *VisualStudioInstallPath*

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Reinicie la sesión de depuración.

> [!NOTE]
> Si desea utilizar un visualizador administrado para la depuración remota, copie el archivo DLL en la misma ruta de acceso en el equipo remoto.
::: moniker-end

## <a name="see-also"></a>Vea también
- [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)
- [Cómo: Escribir un visualizador](create-custom-visualizers-of-data.md)
