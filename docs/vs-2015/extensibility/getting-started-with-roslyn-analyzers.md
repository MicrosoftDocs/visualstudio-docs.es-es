---
title: Introducción a los analizadores Roslyn Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a712697bafefcf115ce10d110c0ef3a4270c6acd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444991"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Introducción a los analizadores de Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con analizadores de código activos basados en proyectos en Visual Studio, los autores de API pueden enviar análisis de código específico según el dominio como parte de sus paquetes NuGet.  Dado que estos analizadores funcionan con la plataforma de compilador de .NET (denominada en código "Roslyn"), pueden producir advertencias en el código a medida que escribe incluso antes de terminar la línea (no hay que esperar a compilar el código para detectar problemas).  Los analizadores también pueden exponer una corrección automática de código a través del símbolo del sistema de bombilla de Visual Studio para permitirle limpiar el código inmediatamente

## <a name="getting-started"></a>Introducción
[Introducción y tutorial de Roslyn Live Code Analyzers](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Tutorial de adición de correcciones de código: proporcione a los usuarios correcciones para los problemas del analizador](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Introducción y Tutorial de Real World Analyzer Talk](https://channel9.msdn.com/events/Build/2015/3-725)

[Analizador Roslyn del mundo real](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que también se puede ver como una [charla](https://channel9.msdn.com/events/Build/2015/3-725)

[Varios ejemplos en GitHub, agrupados en tres tipos de analizadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Introducción y recorrido de unos pocos analizadores hablan](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Otros recursos
[Más documentos en el sitio de GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Reglas de FxCop implementadas con analizadores Roslyn en GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
