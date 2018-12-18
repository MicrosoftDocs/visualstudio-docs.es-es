---
title: Plataforma del compilador .NET (&quot;Roslyn&quot;) extensibilidad | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de01ec4f857042c6eaaaa70632b28cfc830886cb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817092"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Extensibilidad de la plataforma de compilación .NET (&quot;Roslyn&quot;)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La misión principal de .NET Compiler Platform («Roslyn») es la apertura de los compiladores de C# y Visual Basic y al permitir que herramientas y tienen a los desarrolladores compartir en los compiladores de información completa acerca de los programas. Herramientas de análisis de código mejoran la calidad del código y generadores de ayuda en la construcción de la aplicación de código. Como las herramientas de obtención más inteligentes, necesitará tener acceso a cada vez más del conocimiento profundo de código que solo los compiladores poseen. En lugar de traductores opacos (código fuente y código de objeto out), los compiladores de Roslyn ofrecen API que puede usar para tareas relacionadas con el código en las herramientas y aplicaciones.  
  
 Lo mejor es que los compiladores de Roslyn, sus API, ejemplos y tutoriales y las verdaderas herramientas que se basan en estas API son código abierto totalmente en [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Vaya al sitio de OSS para obtener más información y empezar a trabajar con Roslyn. Encontrará vínculos para obtener la más reciente de C# y VB características que puede usar como un usuario final, así como vínculos para empezar a trabajar como un generador de herramienta aprovechando las APIs Roslyn.  
  
## <a name="see-also"></a>Vea también  
 [Introducción a los analizadores de Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)

