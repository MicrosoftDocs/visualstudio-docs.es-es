---
title: para instalar un visualizador | Microsoft Docs
description: Obtenga información sobre cómo instalar un visualizador para que esté disponible para su uso en la depuración en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 611347acfe48e561653d644097d56d029b6a4fa6
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298262"
---
# <a name="how-to-install-a-visualizer"></a>Procedimiento Instalación de un visualizador
Después de crear un visualizador, hay que instalarlo para que esté disponible en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Instalar un visualizador es un proceso sencillo.

> [!NOTE]
> En las aplicaciones UWP, solo se admiten los visualizadores de texto estándar, HTML, XML y JSON. No se admiten los visualizadores personalizados (creados por el usuario).

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Para instalar un visualizador para Visual Studio 2019

1. Busque el archivo DLL que contiene el visualizador que ha compilado.

   Normalmente, es mejor que tanto el archivo DLL del depurador como el archivo DLL del elemento depurado especifiquen **Cualquier CPU** como plataforma de destino. El archivo DLL del depurador debe ser **Cualquier CPU** o **32 bits**. La plataforma de destino para el archivo DLL depurado se debe corresponder con el proceso del elemento depurado.

   >[!NOTE]
   > El visualizador del lado del depurador se carga en el proceso de Visual Studio, por lo que debe ser un archivo DLL de .NET Framework. El lado del elemento depurado puede ser de .NET Framework o .NET Standard, en función del proceso que se depure en Visual Studio.

2. Copie el archivo DLL del [lado de depurador](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (y todos los archivos DLL de los que dependa) en cualquiera de las ubicaciones siguientes:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Copie el archivo DLL del [lado depurado](create-custom-visualizers-of-data.md#to-create-the-visualizer-object-source-for-the-debuggee-side) en cualquiera de las ubicaciones siguientes:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\` *VisualStudioVersion* `\Visualizers\` *Framework*

    donde *Framework* puede ser cualquiera de los siguientes:
    - `net2.0` para los elementos depurados que ejecutan el entorno de ejecución `.NET Framework`.
    - `netstandard2.0` para los elementos depurados que usan un entorno de ejecución que admite `netstandard 2.0` (`.NET Framework v4.6.1+` o `.NET Core 2.0+`).
    - `netcoreapp` para los elementos depurados que ejecutan el entorno de ejecución `.NET Core` (se admite `.NET Core 2.0+`).

   Un archivo DLL del lado depurado es necesario si desea crear un visualizador independiente. Este archivo DLL contiene código para el objeto de datos, que puede implementar métodos de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.

   Si el código del lado depurado está pensado para emplearse en varios destinos, el archivo DLL del lado depurado debe colocarse en la carpeta para la versión de TFM compatible mínima.

4. Reinicie la sesión de depuración.

> [!NOTE]
> El procedimiento es diferente en Visual Studio 2017 y versiones posteriores. Consulte la [versión anterior](how-to-install-a-visualizer.md?view=vs-2017&preserve-view=true) de este artículo.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Para instalar un visualizador para Visual Studio 2017 y versiones posteriores

> [!IMPORTANT]
> En Visual Studio 2017 y versiones posteriores solo se admiten visualizadores de .NET Framework.

1. Busque el archivo DLL que contiene el visualizador que ha compilado.

2. Copie el archivo DLL a una de las siguientes ubicaciones:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Reinicie la sesión de depuración.

> [!NOTE]
> Si desea utilizar un visualizador administrado para la depuración remota, copie el archivo DLL en la misma ruta de acceso en el equipo remoto.
::: moniker-end

## <a name="see-also"></a>Vea también
- [Create Custom Visualizers](../debugger/create-custom-visualizers-of-data.md) (Crear visualizadores personalizados)
- [Cómo: Escritura de un visualizador](create-custom-visualizers-of-data.md)
