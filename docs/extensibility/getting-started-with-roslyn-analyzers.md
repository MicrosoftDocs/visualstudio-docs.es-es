---
title: Introducción a los analizadores de Roslyn | Microsoft Docs
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb224d1c84f9216ed303c919118af4997be2405c
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835908"
---
# <a name="get-started-with-roslyn-analyzers"></a>Introducción a los analizadores de Roslyn

Con los analizadores de código en vivo, basado en el proyecto en Visual Studio, los creadores de API pueden enviar el análisis de código específico de dominio como parte de sus paquetes de NuGet. Dado que estos analizadores cuentan con la plataforma del compilador .NET (denominada "Roslyn"), pueden producir advertencias en el código a medida que escribe, incluso antes de que haya terminado la línea (no necesario esperar a compilar el código para detectar problemas). Los analizadores también pueden aparecer una corrección automática de código mediante el símbolo del sistema de bombilla de Visual Studio para permitir que el código de limpieza inmediatamente.

## <a name="get-started"></a>Primeros pasos

[Información general de los analizadores de Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Tutorial: Escribir la primera corrección analizador y el código](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Agregue las correcciones de código Tutorial: Proporcionar las correcciones de los usuarios para los problemas del analizador](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Analizador de Roslyn del mundo real](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que también puede ver como un [hablar](https://channel9.msdn.com/events/Build/2015/3-725)

[Varios ejemplos en GitHub, se agrupan en tres tipos de analizadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)


## <a name="see-also"></a>Vea también

- [Referencia de versión de paquete de .NET del compilador plataforma](roslyn-version-support.md)
- [Más documentos en el sitio de GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Reglas de FxCop implementadas con analizadores de Roslyn](http://roslynanalyzersstatus.azurewebsites.net/)
