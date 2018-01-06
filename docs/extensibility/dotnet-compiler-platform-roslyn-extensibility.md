---
title: .NET compiler Platform (&quot;Roslyn&quot;) extensibilidad | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b292593c6a6c426bb184acd67a920b5e76e3a51f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET compiler Platform (&quot;Roslyn&quot;) extensibilidad
La misión de núcleo de .NET Compiler Platform («Roslyn») se abre los compiladores de C# y Visual Basic que permite herramientas y tienen a los desarrolladores compartir en los compiladores con información detallada acerca de los programas. Herramientas de análisis de código mejoran la calidad del código y generadores de ayuda en la creación de aplicaciones de código. Medida herramientas le resulte más inteligentes, necesitará tener acceso a cada vez más de los conocimientos de código profundo compiladores solo poseen. En lugar de traductores opacos (código fuente y el código de objeto out), los compiladores Roslyn proporcionan API que puede usar para tareas relacionadas con el código de las herramientas y aplicaciones.  
  
 Lo mejor de todo es que los compiladores Roslyn, sus API, ejemplos y tutoriales y las herramientas reales creadas a partir de estas API son totalmente abierto en [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Vaya al sitio de OSS para obtener más información y empezar a trabajar con Roslyn. Encontrará vínculos para obtener más reciente de C# y características VB que se pueden utilizar como un usuario final, así como vínculos a empezar a trabajar como un generador de herramienta aprovecha las APIs Roslyn.  
  
## <a name="see-also"></a>Vea también  
 [Introducción a los analizadores de Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)