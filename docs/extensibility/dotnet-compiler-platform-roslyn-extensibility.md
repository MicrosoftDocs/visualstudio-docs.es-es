---
title: Extensibilidad de&quot;.NET&quot;Compiler Platform ( Roslyn ) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62ceac6e2be8a0a84d82f6b86b685c7c8b20a182
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712074"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Extensibilidad de&quot;.NET&quot;Compiler Platform ( Roslyn )
La misión principal de la plataforma de compiladores de .NET ("Roslyn") es abrir los compiladores de C y Visual Basic y permitir que las herramientas y los desarrolladores compartan la información enriquecida que los compiladores tienen sobre los programas. Las herramientas de análisis de código mejoran la calidad del código y los generadores de código ayudan en la construcción de aplicaciones. A medida que las herramientas se vuelven más inteligentes, necesitan acceso a más y más conocimientos de código profundos que solo poseen los compiladores. En lugar de ser traductores opacos (entrada de código fuente y código de objeto), los compiladores de Roslyn ofrecen API que puede usar para tareas relacionadas con el código en sus herramientas y aplicaciones.

 La mejor parte es que los compiladores de Roslyn, sus API, ejemplos y tutoriales, y las herramientas reales creadas sobre estas API son todos de código abierto en [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Por favor, vaya al sitio de OSS para obtener más información y empezar a usar Roslyn. Encontrará vínculos para obtener las características más recientes de Visual Basic y de C. que puede usar como usuario final, así como vínculos para empezar a usar como generador de herramientas aprovechando las API de Roslyn.

## <a name="see-also"></a>Vea también
- [Comience con los analizadores Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
