---
title: Plataforma del compilador .NET (&quot;Roslyn&quot;) extensibilidad | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b910d1eb8dcbbe6696c447a7c3a94db533dbbcb3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347904"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET compiler Platform (&quot;Roslyn&quot;) extensibilidad
La misión principal de .NET Compiler Platform («Roslyn») es la apertura de los compiladores de C# y Visual Basic y al permitir que herramientas y tienen a los desarrolladores compartir en los compiladores de información completa acerca de los programas. Herramientas de análisis de código mejoran la calidad del código y generadores de ayuda en la construcción de la aplicación de código. Como las herramientas de obtención más inteligentes, necesitará tener acceso a cada vez más del conocimiento profundo de código que solo los compiladores poseen. En lugar de traductores opacos (código fuente y código de objeto out), los compiladores de Roslyn ofrecen API que puede usar para tareas relacionadas con el código en las herramientas y aplicaciones.

 Lo mejor es que los compiladores de Roslyn, sus API, ejemplos y tutoriales y las verdaderas herramientas que se basan en estas API son código abierto totalmente en [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Vaya al sitio de OSS para obtener más información y empezar a trabajar con Roslyn. Encontrará vínculos para obtener la versión más reciente C# y características de Visual Basic que puede usar como un usuario final, así como vínculos para empezar a trabajar como un generador de herramienta aprovechando las APIs Roslyn.

## <a name="see-also"></a>Vea también
- [Introducción a los analizadores de Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)