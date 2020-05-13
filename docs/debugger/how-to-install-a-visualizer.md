---
title: 'Cómo: Instalar un visualizador ? Microsoft Docs'
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
ms.openlocfilehash: 499d644cc8374b070cedaf058b0e4dc17d155bdc
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880265"
---
# <a name="how-to-install-a-visualizer"></a>Cómo: Instalar un visualizador
Después de crear un visualizador, hay que instalarlo para que esté disponible en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalar un visualizador es un proceso sencillo.

> [!NOTE]
> En las aplicaciones para UWP, solo se admiten los visualizadores de texto estándar, HTML, XML y JSON. No se admiten los visualizadores personalizados (creados por el usuario).

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Para instalar un visualizador para Visual Studio 2019
  
1. Busque el archivo DLL que contiene el visualizador que ha creado.

   Normalmente, es mejor si tanto el archivo DLL del lado del depurador como el archivo DLL del lado del depurador especifican **Cualquier CPU** como plataforma de destino. El archivo DLL del lado del depurador debe ser **Cualquier CPU** o **32 bits.** La plataforma de destino para el archivo DLL del lado del depurador debe corresponder al proceso del depurador.

2. Copie el archivo DLL del [lado](create-custom-visualizers-of-data.md#to-create-the-debugger-side) del depurador (y los archivos DLL de los que depende) en cualquiera de las siguientes ubicaciones:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Copie el archivo DLL del [lado de Depuración](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) en cualquiera de las siguientes ubicaciones:

    - *Marco de VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\`*Marco de VisualStudioVersion* `\Visualizers\` *Framework*

    donde *Marco* es:
    - `net2.0`para los debuggees que ejecutan el `.NET Framework` tiempo de ejecución.
    - `netstandard2.0`para debuggees usando `netstandard 2.0` un`.NET Framework v4.6.1+` `.NET Core 2.0+`tiempo de ejecución que admite ( o ).
    - `netcoreapp`para los debuggees que ejecutan el `.NET Core` tiempo de ejecución. (soporta) `.NET Core 2.0+`

4. Reinicie la sesión de depuración.

> [!NOTE]
> El procedimiento es diferente en Visual Studio 2017 y versiones anteriores. Consulte la [versión anterior](how-to-install-a-visualizer.md?view=vs-2017) de este artículo.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Para instalar un visualizador para Visual Studio 2017 y versiones anteriores

> [!IMPORTANT]
> En Visual Studio 2017 y versiones anteriores solo se admiten visualizadores de .NET Framework.

1. Busque el archivo DLL que contiene el visualizador que ha compilado.

2. Copie el archivo DLL a una de las siguientes ubicaciones:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Reinicie la sesión de depuración.

> [!NOTE]
> Si desea utilizar un visualizador administrado para la depuración remota, copie el archivo DLL en la misma ruta de acceso en el equipo remoto.
::: moniker-end

## <a name="see-also"></a>Vea también
- [Creación de visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md)
- [Cómo: Escribir un visualizador](create-custom-visualizers-of-data.md)
