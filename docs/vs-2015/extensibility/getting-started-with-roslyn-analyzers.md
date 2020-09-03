---
title: Introducción con analizadores de Roslyn | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a712697bafefcf115ce10d110c0ef3a4270c6acd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444991"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Introducción a los analizadores de Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con los analizadores de código basados en proyectos activos en Visual Studio, los autores de la API pueden enviar análisis de código específico del dominio como parte de sus paquetes de NuGet.  Dado que estos analizadores se basan en el .NET Compiler Platform (con el nombre de código "Roslyn"), pueden generar advertencias en el código a medida que se escriben incluso antes de que se haya terminado la línea (no hay más que esperar a compilar el código para detectar problemas).  Los analizadores también pueden mostrar una corrección de código automática a través del aviso de bombillas de Visual Studio para que pueda limpiar el código inmediatamente.

## <a name="getting-started"></a>Introducción
[Tutorial de introducción y análisis de código en vivo de Roslyn](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Tutorial para agregar correcciones de código: proporcionar a los usuarios correcciones para problemas del analizador](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Introducción y tutorial del analizador del mundo real](https://channel9.msdn.com/events/Build/2015/3-725)

[Analizador Roslyn real](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que también puede ver como una [charla](https://channel9.msdn.com/events/Build/2015/3-725)

[Varios ejemplos de GitHub, agrupados en tres tipos de analizadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Introducción y paseo por algunos analizadores](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Otros recursos
[Más documentos en el sitio OSS de GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Reglas de FxCop implementadas con analizadores de Roslyn en GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
