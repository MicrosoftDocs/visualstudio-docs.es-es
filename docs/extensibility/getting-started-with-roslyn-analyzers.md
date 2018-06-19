---
title: Introducción a los analizadores de Roslyn | Documentos de Microsoft
ms.date: 04/02/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7b887703343dab10f9cc1f0cbf8e2e2b37b0065b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126814"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Introducción a los analizadores de Roslyn

Con los analizadores de código en vivo, basado en el proyecto en Visual Studio, los autores de API pueden distribuir el análisis de código específico de dominio como parte de sus paquetes de NuGet. Dado que estos analizadores cuentan con la tecnología .NET Compiler Platform («Roslyn» Code-named), pueden generar advertencias en el código a medida que escribe, incluso antes de que haya terminado de la línea (espera nada más para compilar el código para detectar problemas). Los analizadores pueden aparecer también una corrección automática de código mediante el símbolo del sistema de bombilla de Visual Studio para permitir que el código de limpieza inmediatamente.

## <a name="getting-started"></a>Introducción

[Los analizadores de código activo Roslyn introducción y tutorial](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Agregar código corrige Tutorial: Proporcionar correcciones de los usuarios para problemas de analizador](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Introducción y Tutorial del mundo Real analizador Talk](http://channel9.msdn.com/events/Build/2015/3-725)

[Real World Roslyn analizador](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que también puede ver como un [hablar](http://channel9.msdn.com/events/Build/2015/3-725)

[Varios ejemplos en github, se agrupan en tres tipos de analizadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Introducción y paseo de analizadores unos hablar](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="see-also"></a>Vea también

- [Información general de los analizadores de Roslyn](../code-quality/roslyn-analyzers-overview.md)
- [Más documentos en el sitio de github OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Reglas de FxCop implementadas con analizadores de Roslyn en github](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)