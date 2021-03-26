---
title: Extensibilidad de .NET Compiler Platform ( &quot; Roslyn &quot; ) | Microsoft Docs
description: Obtenga información sobre el .NET Compiler Platform, que permite que las herramientas y los desarrolladores compartan en los compiladores de información enriquecida de los programas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: af9be2c4a57763b4521f3564e95c760e5bdd566d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091167"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Extensibilidad de .NET Compiler Platform ( &quot; Roslyn &quot; )
La principal misión del .NET Compiler Platform ("Roslyn") es abrir los compiladores de C# y Visual Basic y permitir que las herramientas y los desarrolladores compartan en los compiladores de información enriquecida de los programas. Las herramientas de análisis de código mejoran la calidad del código y los generadores de código ayudan a la construcción de la aplicación. A medida que las herramientas se hacen más inteligentes, necesitan tener acceso a más de un conocimiento profundo del código que solo poseen los compiladores. En lugar de ser traductores opacos (código fuente en y código de objeto), los compiladores Roslyn ofrecen las API que puede usar para las tareas relacionadas con el código en las herramientas y aplicaciones.

 Lo mejor es que los compiladores de Roslyn, sus API, los ejemplos y los tutoriales, así como las herramientas reales creadas sobre estas API, son totalmente de código abierto en [github.com/dotnet/Roslyn](https://github.com/dotnet/Roslyn). Vaya al sitio de OSS para obtener más información y empiece a trabajar con Roslyn. Encontrará vínculos para obtener las características más recientes de C# y Visual Basic que puede usar como usuario final, así como vínculos para empezar a trabajar como un generador de herramientas que aprovecha las API de Roslyn.

## <a name="see-also"></a>Consulte también
- [Introducción a los analizadores de Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
