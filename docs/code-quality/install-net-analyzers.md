---
title: Habilitación o instalación de analizadores de .NET propios
ms.date: 08/03/2018
description: Obtenga información sobre cómo habilitar analizadores de .NET propios desde el SDK de .NET o instalar estos analizadores como un paquete de NuGet.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: b41615e1826987cb42076ab3195fe7bfad235e7a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867898"
---
# <a name="enable-or-install-first-party-net-analyzers"></a>Habilitación o instalación de analizadores de .NET propios

## <a name="overview"></a>Información general

Los analizadores de .NET Compiler Platform (Roslyn) inspeccionan el código de C# o Visual Basic para supervisar la calidad del código y verificar si contiene problemas de estilo. Los analizadores de .NET propios son **independientes de la plataforma de destino**. Es decir, el proyecto no necesita tener como destino una plataforma .NET específica. Los analizadores funcionan para los proyectos que tienen `net5.0` como destino y versiones anteriores de .net, como `netcoreapp` , `netstandard` y `net472` .

Puede habilitar o instalar los analizadores de .NET propios de una de las siguientes maneras:

- **Habilitar desde el SDK de .net**: a partir de Visual Studio 2019 16,8 y .net 5,0, estos analizadores se [incluyen con el SDK de .net](/dotnet/fundamentals/code-analysis/overview). De forma predeterminada, el análisis se habilita para los proyectos que tienen como destino .NET 5,0 o posterior. Puede habilitar el análisis de código en los proyectos que tienen como destino versiones anteriores de .NET estableciendo la `EnableNETAnalyzers` propiedad en `true` . También puede deshabilitar el análisis de código del proyecto si establece `EnableNETAnalyzers` en `false` .

- **Instalar como un paquete Nuget**: Si no quiere pasar al SDK de .net 5 o si prefiere un modelo basado en paquetes Nuget, los analizadores también están disponibles en el `Microsoft.CodeAnalysis.NetAnalyzers` [paquete nuget](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) en Visual Studio 2019.  Podría preferir un modelo basado en paquetes para las actualizaciones de versión a petición. Si está en Visual Studio 2017, instale en `2.9.x` su lugar la versión más reciente del `Microsoft.CodeAnalysis.FxCopAnalyzers` [paquete de NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) .

> [!NOTE]
> Se recomienda habilitar los analizadores desde el SDK de .NET en lugar de instalar el `Microsoft.CodeAnalysis.NetAnalyzers` [paquete NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers), siempre que sea posible. La habilitación de los analizadores desde el SDK de .NET garantiza la obtención automática de las correcciones de errores del analizador y los nuevos analizadores en cuanto se actualice el SDK. En el modelo de NuGet, debe actualizar el paquete NuGet cada vez que quiera las correcciones de errores más recientes. El paquete NuGet se actualiza con más frecuencia.

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de código en Visual Studio](roslyn-analyzers-overview.md)
- [Uso de analizadores de código en Visual Studio](use-roslyn-analyzers.md)
- [Migración del análisis heredado a los analizadores de .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Migración de los analizadores de FxCop a los de .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
