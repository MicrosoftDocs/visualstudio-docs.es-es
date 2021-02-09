---
title: Migración de los analizadores de FxCop a los de .NET
ms.custom: SEO-VS-2020
description: Obtenga información sobre cómo migrar de los analizadores de FxCop a los analizadores de .NET
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
ms.openlocfilehash: e435502587e65bd694567f4100516a91fa97cc0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867872"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Migración de los analizadores de FxCop a los de .NET

El análisis de código fuente por .NET Compiler Platform ("Roslyn") reemplaza el [análisis heredado](code-analysis-for-managed-code-overview.md) de código administrado. Muchas de las reglas de análisis heredado (FxCop) ya se han reescrito como analizadores de origen.

Antes de Visual Studio 2019 16,8 y .NET 5,0, estos analizadores se distribuyen como `Microsoft.CodeAnalysis.FxCopAnalyzers` [paquete NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).

A partir de Visual Studio 2019 16,8 y .NET 5,0, estos analizadores se [incluyen con el SDK de .net](/dotnet/fundamentals/code-analysis/overview). Si no desea pasar al SDK de .NET 5 o si prefiere un modelo basado en paquetes NuGet, los analizadores también están disponibles en el `Microsoft.CodeAnalysis.NetAnalyzers` [paquete Nuget](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). Podría preferir un modelo basado en paquetes para las actualizaciones de versión a petición.

> [!NOTE]
> Los analizadores de .NET propios son independientes de la plataforma de destino. Es decir, el proyecto no necesita tener como destino una plataforma .NET específica. Los analizadores funcionan para los proyectos que tienen `net5.0` como destino y versiones anteriores de .net, como `netcoreapp` , `netstandard` y `net472` .

## <a name="migration-steps"></a>Pasos de migración

A partir de la versión `3.3.2` , el `Microsoft.CodeAnalysis.FxCopAnalyzers` paquete NuGet está en desuso. Siga los pasos que se indican a continuación para migrar el proyecto o la solución de `Microsoft.CodeAnalysis.FxCopAnalyzers` a los analizadores de .net:

1. Desinstalar el `Microsoft.CodeAnalysis.FxCopAnalyzers` paquete NuGet

2. [Habilitar o instalar analizadores de .net](install-net-analyzers.md). Tenga en cuenta que no es necesario cambiar la plataforma de destino del proyecto.

3. Habilitar reglas adicionales: `Microsoft.CodeAnalysis.NetAnalyzers` es mucho más conservador en comparación con `Microsoft.CodeAnalysis.FxCopAnalyzers` . A diferencia del paquete FxCopAnalyzers, solo tiene algunas reglas de corrección que están [habilitadas de forma predeterminada como advertencias de compilación](/dotnet/fundamentals/code-analysis/overview#enabled-rules). Puede [Habilitar otras reglas](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) mediante la personalización de la propiedad [AnalysisMode](/dotnet/core/project-sdk/msbuild-props#analysismode) de MSBuild. Por ejemplo, al establecer la propiedad en, `AllEnabledByDefault` se habilitarán todas las reglas de CA aplicables como advertencias de compilación de forma predeterminada.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Vea también

- [Análisis de código fuente frente a análisis heredado](net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)
- [Migración del análisis heredado a los analizadores de .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Habilitar o instalar analizadores de .NET](install-net-analyzers.md)
- [Preguntas más frecuentes sobre los analizadores de .NET](net-analyzers-faq.md)
- [Configurar analizadores de .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
