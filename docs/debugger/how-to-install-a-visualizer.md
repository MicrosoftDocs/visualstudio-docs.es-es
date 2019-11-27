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
ms.openlocfilehash: 1df72c6978f5ab34a86c74dbc1ea349db5aa4457
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491306"
---
# <a name="how-to-install-a-visualizer"></a>Cómo: Instalar un visualizador
Después de crear un visualizador, hay que instalarlo para que esté disponible en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalar un visualizador es un proceso sencillo.

> [!NOTE]
> En las aplicaciones para UWP, solo se admiten los visualizadores estándar de texto, HTML, XML y JSON. No se admiten los visualizadores personalizados (creados por el usuario).

### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Para instalar un visualizador para Visual Studio 2019
  
1. Busque el archivo DLL que contiene el visualizador que ha compilado.

2. Copie el archivo dll [del lado depurador](create-custom-visualizers-of-data.md#to-create-the-debugger-side) en cualquiera de las siguientes ubicaciones:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Copie la dll del [lado depurado](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) en cualquiera de las siguientes ubicaciones:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\` *VisualStudioVersion* `\Visualizers\` *Framework*

    Donde *Framework* es:
    - `net2.0` para depuraciones que ejecutan el tiempo de ejecución de `.NET Framework`.
    - `netstandard2.0` para depurar a través de un tiempo de ejecución que admite `netstandard 2.0` (`.NET Framework v4.6.1+` o `.NET Core 2.0+`).
    - `netcoreapp` para depuraciones que ejecutan el tiempo de ejecución de `.NET Core`. (admite `.NET Core 2.0+`)

4. Reinicie la sesión de depuración.

### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Para instalar un visualizador para Visual Studio 2017 y versiones anteriores

> [!IMPORTANT]
> Solo se admiten los visualizadores de .NET Framework en Visual Studio 2017 y versiones anteriores

1. Busque el archivo DLL que contiene el visualizador que ha compilado.

2. Copie el archivo DLL a una de las siguientes ubicaciones:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Reinicie la sesión de depuración.

> [!NOTE]
> Si desea utilizar un visualizador administrado para la depuración remota, copie el archivo DLL en la misma ruta de acceso en el equipo remoto.

## <a name="see-also"></a>Vea también
- [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)
- [Cómo: Escribir un visualizador](create-custom-visualizers-of-data.md)
