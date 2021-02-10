---
title: Introducción con analizadores de Roslyn | Microsoft Docs
description: Use estos recursos para empezar a trabajar con los analizadores de Roslyn en Visual Studio; incluye un tutorial y varios ejemplos.
ms.custom: SEO-VS-2020
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e12c418365ad7127823a115aa1ed66b06ff6e156
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945817"
---
# <a name="get-started-with-roslyn-analyzers"></a>Introducción a los analizadores de Roslyn

Con los analizadores de código basados en proyectos activos en Visual Studio, los autores de la API pueden enviar análisis de código específico del dominio como parte de sus paquetes de NuGet. Dado que estos analizadores se basan en el .NET Compiler Platform (con el nombre de código "Roslyn"), pueden generar advertencias en el código a medida que se escriben incluso antes de que se haya terminado la línea (no hay más que esperar a compilar el código para detectar problemas). Los analizadores también pueden mostrar una corrección de código automática a través del aviso de bombilla de Visual Studio para que pueda limpiar el código inmediatamente.

## <a name="get-started"></a>Introducción

[Información general de los analizadores de Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Tutorial: Crear el primer analizador y la corrección de código](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Tutorial para agregar correcciones de código: proporcionar correcciones a los usuarios para problemas del analizador](/archive/msdn-magazine/2015/february/csharp-adding-a-code-fix-to-your-roslyn-analyzer)

[Analizador Roslyn real](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que también puede ver como una [charla](https://channel9.msdn.com/events/Build/2015/3-725)

[Varios ejemplos de GitHub, agrupados en tres tipos de analizadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Vea también

- [Referencia de versión del paquete de .NET Compiler Platform](roslyn-version-support.md)
- [Más documentos en el sitio OSS de GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Reglas de FxCop implementadas con analizadores de Roslyn](../code-quality/fxcop-rule-port-status.md)
