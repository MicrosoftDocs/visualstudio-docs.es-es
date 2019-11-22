---
title: Getting Started with Roslyn Analyzers | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d45491fe031c01a31812f5ed4944f76d059cd60
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300012"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Introducción a los analizadores de Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

With live, project-based code analyzers in Visual Studio, API authors can ship domain-specific code analysis as part of their NuGet packages.  Because these analyzers are powered by the .NET Compiler Platform (code-named “Roslyn”), they can produce warnings in your code as you type even before you’ve finished the line (no more waiting to build your code to discover issues).  Analyzers can also surface an automatic code fix through the Visual Studio light bulb prompt to let you clean up your code immediately

## <a name="getting-started"></a>Introducción
[Roslyn Live Code Analyzers Introduction and Walkthrough](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Adding Code Fixes Walkthrough: Provide Users Fixes for Analyzer Issues](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Introduction and Walkthrough of Real World Analyzer Talk](https://channel9.msdn.com/events/Build/2015/3-725)

[Real World Roslyn Analyzer](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) that you can also watch as a [talk](https://channel9.msdn.com/events/Build/2015/3-725)

[Several examples on GitHub, grouped into three kinds of analyzers](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Introduction and Tour of a Few Analyzers Talk](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Otros recursos
[More docs on the GitHub OSS site](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[FxCop rules implemented with Roslyn analyzers on GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
