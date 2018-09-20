---
title: Introducción a los analizadores de Roslyn | Microsoft Docs
ms.date: 04/02/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 41db830fbf7dcbe97f44d64ffa9b9701ec658c1e
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370593"
---
# <a name="get-started-with-roslyn-analyzers"></a>Introducción a los analizadores de Roslyn

Con los analizadores de código en vivo, basado en el proyecto en Visual Studio, los creadores de API pueden enviar el análisis de código específico de dominio como parte de sus paquetes de NuGet. Dado que estos analizadores cuentan con la plataforma del compilador .NET (denominada "Roslyn"), pueden producir advertencias en el código a medida que escribe, incluso antes de que haya terminado la línea (no necesario esperar a compilar el código para detectar problemas). Los analizadores también pueden aparecer una corrección automática de código mediante el símbolo del sistema de bombilla de Visual Studio para permitir que el código de limpieza inmediatamente.

## <a name="get-started"></a>Primeros pasos

[Tutorial e introducción de los analizadores de código en directo de Roslyn](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Agregar código de correcciones de tutorial: proporcionar correcciones de los usuarios para los problemas del analizador](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Introducción y Tutorial del analizador del mundo real de hablar](https://channel9.msdn.com/events/Build/2015/3-725)

[Analizador de Roslyn del mundo real](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que también puede ver como un [hablar](https://channel9.msdn.com/events/Build/2015/3-725)

[Varios ejemplos en github, se agrupan en tres tipos de analizadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Introducción y visita guiada de algunos analizadores hablar](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de Roslyn](../code-quality/roslyn-analyzers-overview.md)
- [Más documentos en el sitio de github de OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Reglas de FxCop implementadas con analizadores de Roslyn en GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)