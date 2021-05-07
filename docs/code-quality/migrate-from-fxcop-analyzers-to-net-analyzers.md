---
title: Migración de los analizadores de FxCop a los de .NET
ms.custom: SEO-VS-2020
description: Aprenda a migrar de analizadores de FxCop a analizadores de .NET.
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: d6f9c36b1b64abe648c3aa9014c633e4e4949b1a
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798263"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Migración de los analizadores de FxCop a los de .NET

El análisis de código .NET Compiler Platform analizadores ("Roslyn") reemplaza [el análisis heredado](code-analysis-for-managed-code-overview.md) para el código administrado. Muchas de las reglas de análisis heredado (FxCop) ya se han reescrito como analizadores de origen.

Antes de Visual Studio 2019 16.8 y .NET 5.0, estos analizadores se suministran como paquete `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).

A partir Visual Studio 2019 16.8 y .NET 5.0, estos analizadores se incluyen con el [SDK de .NET.](/dotnet/fundamentals/code-analysis/overview) Si no desea pasar al SDK de .NET 5+ o si prefiere un modelo basado en paquetes NuGet, los analizadores también están disponibles en el paquete `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Es posible que prefiera un modelo basado en paquetes para las actualizaciones de versión a petición.

> [!NOTE]
> Los analizadores de .NET de origen son independientes de la plataforma de destino. Es decir, el proyecto no necesita tener como destino una plataforma .NET específica. Los analizadores funcionan para proyectos que tienen como destino, así como versiones anteriores de `net5.0` .NET, como `netcoreapp` `netstandard` , y `net472` .

## <a name="migration-steps"></a>Pasos de migración

A partir de la `3.3.2` versión , el paquete `Microsoft.CodeAnalysis.FxCopAnalyzers` NuGet ha quedado en desuso. Siga estos pasos para migrar el proyecto o la solución de `Microsoft.CodeAnalysis.FxCopAnalyzers` a los analizadores de .NET:

1. Desinstalación `Microsoft.CodeAnalysis.FxCopAnalyzers` del paquete NuGet

2. [Habilite o instale analizadores de .NET.](install-net-analyzers.md) Tenga en cuenta que no es necesario cambiar la plataforma de destino del proyecto.

3. Habilitar reglas adicionales: `Microsoft.CodeAnalysis.NetAnalyzers` es mucho más conservador en comparación con `Microsoft.CodeAnalysis.FxCopAnalyzers` . A diferencia del paquete FxCopAnalyzers, solo tiene algunas reglas de corrección que están habilitadas de forma predeterminada [como advertencias de compilación](/dotnet/fundamentals/code-analysis/overview#enabled-rules). Puede habilitar [reglas adicionales personalizando](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) la [propiedad AnalysisMode](/dotnet/core/project-sdk/msbuild-props#analysismode) de MSBuild. Por ejemplo, establecer la propiedad en habilitará todas las reglas de `AllEnabledByDefault` CA aplicables como advertencias de compilación de forma predeterminada.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Consulte también

- [Análisis de código fuente frente a análisis heredado](net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)
- [Migración del análisis heredado a los analizadores de .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Habilitación o instalación de analizadores de .NET](install-net-analyzers.md)
- [Preguntas más frecuentes sobre los analizadores de .NET](net-analyzers-faq.yml)
- [Configuración de analizadores de .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
