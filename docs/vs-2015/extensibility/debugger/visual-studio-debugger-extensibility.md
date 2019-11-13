---
title: Extensibilidad del depurador de Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b8d37954bf238b2ed1323bf021fded94ec0c584
ms.sourcegitcommit: 3a19319e2599bd193fb2ca32020ca53942974bfd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "73983668"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilidad del depurador de Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio incluye un depurador de código fuente completamente interactivo, que proporciona una herramienta eficaz y fácil de usar para realizar un seguimiento de los errores del programa. El depurador ha completado la compatibilidad C#Visual Basic,,C++C/y JavaScript. Sin embargo, con el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], que está disponible en el [centro de descarga de Microsoft](https://www.microsoft.com/download/details.aspx?id=21835), se pueden admitir otros lenguajes de programación en el depurador con las mismas características enriquecidas.  
  
 El depurador de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] es el front-end común (es decir, la interfaz de usuario) para los componentes de depuración que, a su vez, son específicos del lenguaje que se depura. En el caso de los nuevos idiomas, todo lo que se necesita para la compatibilidad con el depurador de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] es crear los componentes de back-end necesarios, como un motor DE depuración (DE). Es donde entra en el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
 El [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] incluye una referencia completa a todos los elementos [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] necesarios para crear un nuevo DE. Además, hay ejemplos y tutoriales que le ayudarán a empezar.  
  
 Para obtener un ejemplo de un extremo a otro de un sistema de proyectos de lenguaje con compatibilidad para la depuración, consulte el [ejemplo de IronPython](https://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 En las secciones siguientes se describe cómo extender el depurador mediante el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
## <a name="in-this-section"></a>En esta sección  
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Describe qué ofrece [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] las ofertas de depuración y cómo instalar el SDK.  
  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Documenta el proceso personalizado DE, desde preparar el programa para un DE para desasociar DE.  
  
 [Escritura de un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Explica si debe escribir un evaluador de expresiones.  
  
 [Elección de una estrategia de implementación del motor de depuración](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Describe cómo implementar su DE.  
  
 [Referencia](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Documenta la API de depuración de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Muestras](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Contiene vínculos a un ejemplo del evaluador de expresiones Common Language Runtime y un ejemplo del motor de depuración.
