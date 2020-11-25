---
title: Habilitar o instalar analizadores de .NET
ms.date: 08/03/2018
description: Obtenga información sobre cómo habilitar los analizadores de .NET desde el SDK de .NET o instalar estos analizadores como un paquete NuGet.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a14d89caba498a07c2447f9df1109e4da9f6a466
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112188"
---
# <a name="enable-or-install-net-analyzers"></a>Habilitar o instalar analizadores de .NET

## <a name="overview"></a>Información general

Los analizadores de .NET Compiler Platform (Roslyn) inspeccionan el código de C# o Visual Basic para supervisar la calidad del código y verificar si contiene problemas de estilo. Puede habilitar o instalar estos analizadores de una de las siguientes maneras:

- **Habilitar desde el SDK de .net**: a partir de Visual Studio 2019 16,8 y .net 5,0, estos analizadores se [incluyen con el SDK de .net](/dotnet/fundamentals/code-analysis/overview). De forma predeterminada, el análisis se habilita para los proyectos que tienen como destino .NET 5,0 o posterior. Puede habilitar el análisis de código en los proyectos que tienen como destino versiones anteriores de .NET estableciendo la `EnableNETAnalyzers` propiedad en `true` . También puede deshabilitar el análisis de código del proyecto si establece `EnableNETAnalyzers` en `false` .

- **Instalar como un paquete Nuget**: como alternativa, puede instalar estos analizadores mediante la instalación del `Microsoft.CodeAnalysis.NetAnalyzers` [paquete de nuget](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) en Visual Studio 2019. Si está en Visual Studio 2017, instale la versión más reciente `2.9.x` del `Microsoft.CodeAnalysis.FxCopAnalyzers` [paquete de NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/).

> [!NOTE]
> Se recomienda habilitar los analizadores desde el SDK de .NET en lugar de instalar el `Microsoft.CodeAnalysis.NetAnalyzers` [paquete NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers), siempre que sea posible. La habilitación de los analizadores desde el SDK de .NET garantiza la obtención automática de las correcciones de errores del analizador y los nuevos analizadores en cuanto se actualice el SDK.

## <a name="see-also"></a>Consulta también

- [Información general de los analizadores de código en Visual Studio](roslyn-analyzers-overview.md)
- [Uso de analizadores de código en Visual Studio](use-roslyn-analyzers.md)
- [Migración de análisis heredado a analizadores de .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Migración de analizadores de FxCop a analizadores de .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)
