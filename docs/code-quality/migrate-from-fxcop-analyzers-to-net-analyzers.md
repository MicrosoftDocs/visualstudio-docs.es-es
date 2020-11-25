---
title: Migración de analizadores de FxCop a analizadores de .NET
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
manager: jillfra
ms.openlocfilehash: b62f99b296c0f9624079423d850029f804e5ebe4
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112196"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>Migración de analizadores de FxCop a analizadores de .NET

El análisis de código fuente por .NET Compiler Platform ("Roslyn") reemplaza el [análisis heredado](code-analysis-for-managed-code-overview.md) de código administrado. Muchas de las reglas de análisis heredado (FxCop) ya se han reescrito como analizadores de origen.

Antes de Visual Studio 2019 16,8 y .NET 5,0, estos analizadores se distribuyen como `Microsoft.CodeAnalysis.FxCopAnalyzers` [paquete NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers).

A partir de Visual Studio 2019 16,8 y .NET 5,0, estos analizadores se [incluyen con el SDK de .net](/dotnet/fundamentals/code-analysis/overview). También están disponibles como `Microsoft.CodeAnalysis.NetAnalyzers` [paquete NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers). `Microsoft.CodeAnalysis.FxCopAnalyzers` Pronto estará en desuso el paquete NuGet.

## <a name="migration-steps"></a>Pasos de migración

Siga los pasos que se indican a continuación para migrar el proyecto o la solución de `Microsoft.CodeAnalysis.FxCopAnalyzers` a los analizadores de .net:

1. Desinstalar el `Microsoft.CodeAnalysis.FxCopAnalyzers` paquete NuGet

2. [Habilitar o instalar analizadores de .NET](install-net-analyzers.md)

3. Habilitar reglas adicionales: `Microsoft.CodeAnalysis.NetAnalyzers` es mucho más conservador en comparación con `Microsoft.CodeAnalysis.FxCopAnalyzers` . A diferencia del paquete FxCopAnalyzers, solo tiene algunas reglas de corrección que están [habilitadas de forma predeterminada como advertencias de compilación](/dotnet/fundamentals/code-analysis/overview#enabled-rules). Puede [Habilitar otras reglas](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) mediante la personalización de la propiedad [AnalysisMode](/dotnet/core/project-sdk/msbuild-props#analysismode) de MSBuild. Por ejemplo, al establecer la propiedad en, `AllEnabledByDefault` se habilitarán todas las reglas de CA aplicables como advertencias de compilación de forma predeterminada.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>Consulta también

- [Análisis de código fuente frente a análisis heredado](net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)
- [Migración de análisis heredado a analizadores de .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Habilitar o instalar analizadores de .NET](install-net-analyzers.md)
- [Preguntas más frecuentes sobre los analizadores de .NET](net-analyzers-faq.md)
- [Configurar analizadores de .NET](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
