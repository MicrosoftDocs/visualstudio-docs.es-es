---
title: Introducción con analizadores de Roslyn | Microsoft Docs
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21b2d77d8c038988fa77293280c9ff7ad38cc82e
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2019
ms.locfileid: "68822345"
---
# <a name="get-started-with-roslyn-analyzers"></a>Introducción a los analizadores de Roslyn

Con los analizadores de código basados en proyectos activos en Visual Studio, los autores de la API pueden enviar análisis de código específico del dominio como parte de sus paquetes de NuGet. Dado que estos analizadores se basan en el .NET Compiler Platform (con el nombre de código "Roslyn"), pueden generar advertencias en el código a medida que se escriben incluso antes de que se haya terminado la línea (no hay más que esperar a compilar el código para detectar problemas). Los analizadores también pueden mostrar una corrección de código automática a través del aviso de bombilla de Visual Studio para que pueda limpiar el código inmediatamente.

## <a name="get-started"></a>Introducción

[Información general de los analizadores de Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Tutorial: Escriba su primer analizador y corrección de código](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Tutorial para agregar correcciones de código: Proporcionar correcciones a los usuarios para problemas del analizador](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Analizador Roslyn real](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que también puede ver como una [charla](https://channel9.msdn.com/events/Build/2015/3-725)

[Varios ejemplos de GitHub, agrupados en tres tipos de analizadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Vea también

- [Referencia de versión del paquete de .NET Compiler Platform](roslyn-version-support.md)
- [Más documentos en el sitio OSS de GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Reglas de FxCop implementadas con analizadores de Roslyn](../code-quality/fxcop-rule-port-status.md)
