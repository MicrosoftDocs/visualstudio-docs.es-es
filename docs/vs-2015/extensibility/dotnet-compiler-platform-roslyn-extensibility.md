---
title: Extensibilidad de .NET Compiler Platform ( &quot; Roslyn &quot; ) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fba277731444a294f276f43cc67b098039f4a64f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204731"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Extensibilidad de la plataforma de compilación .NET (&quot;Roslyn&quot;)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La principal misión del .NET Compiler Platform ("Roslyn") es abrir los compiladores de C# y Visual Basic y permitir que las herramientas y los desarrolladores compartan en los compiladores de información enriquecida de los programas. Las herramientas de análisis de código mejoran la calidad del código y los generadores de código ayudan a la construcción de la aplicación. A medida que las herramientas se hacen más inteligentes, necesitan tener acceso a más de un conocimiento profundo del código que solo poseen los compiladores. En lugar de ser traductores opacos (código fuente en y código de objeto), los compiladores Roslyn ofrecen las API que puede usar para las tareas relacionadas con el código en las herramientas y aplicaciones.  
  
 Lo mejor es que los compiladores de Roslyn, sus API, los ejemplos y los tutoriales, así como las herramientas reales creadas sobre estas API, son totalmente de código abierto en [github.com/dotnet/Roslyn](https://github.com/dotnet/Roslyn). Vaya al sitio de OSS para obtener más información y empiece a trabajar con Roslyn. Encontrará vínculos para obtener las últimas características de C# y VB que puede usar como usuario final, así como vínculos para empezar a trabajar como un generador de herramientas que aprovecha las API de Roslyn.  
  
## <a name="see-also"></a>Consulte también  
 [Introducción a los analizadores de Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
