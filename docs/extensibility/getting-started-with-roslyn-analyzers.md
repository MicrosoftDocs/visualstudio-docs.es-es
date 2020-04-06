---
title: Introducción a los analizadores Roslyn Microsoft Docs
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc975ff4f142b85297c20f16ac399fce588c093b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711274"
---
# <a name="get-started-with-roslyn-analyzers"></a>Comience con los analizadores Roslyn

Con analizadores de código activos basados en proyectos en Visual Studio, los autores de API pueden enviar análisis de código específico según el dominio como parte de sus paquetes NuGet. Dado que estos analizadores funcionan con la plataforma de compilador de .NET (denominada en código "Roslyn"), pueden producir advertencias en el código a medida que escribe incluso antes de terminar la línea (no hay que esperar a compilar el código para detectar problemas). Los analizadores también pueden exponer una corrección automática de código a través del símbolo del sistema de bombilla de Visual Studio para permitirle limpiar el código inmediatamente.

## <a name="get-started"></a>Introducción

[Resumen de analizadores Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Tutorial: Escribir el primer analizador y la corrección del código](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Agregar correcciones de código Tutorial: Proporcionar a los usuarios correcciones para problemas del analizador](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Analizador Roslyn del mundo real](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que también se puede ver como una [charla](https://channel9.msdn.com/events/Build/2015/3-725)

[Varios ejemplos en GitHub, agrupados en tres tipos de analizadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Vea también

- [Referencia de la versión del paquete de plataforma del compilador .NET](roslyn-version-support.md)
- [Más documentos en el sitio de GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Reglas de FxCop implementadas con analizadores Roslyn](../code-quality/fxcop-rule-port-status.md)
