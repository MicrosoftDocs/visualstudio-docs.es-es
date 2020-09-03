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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "73983668"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilidad del depurador de Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio incluye un depurador de código fuente completamente interactivo, que proporciona una herramienta eficaz y fácil de usar para realizar un seguimiento de los errores del programa. El depurador es totalmente compatible Visual Basic, C#, C/C++ y JavaScript. Sin embargo, con el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , que está disponible en el [centro de descarga de Microsoft](https://www.microsoft.com/download/details.aspx?id=21835), se pueden admitir otros lenguajes de programación en el depurador con las mismas características enriquecidas.  
  
 El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depurador es el front-end común (es decir, la interfaz de usuario) para los componentes de depuración que, a su vez, son específicos del lenguaje que se depura. En el caso de los nuevos lenguajes, todo lo que se necesita para que el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depurador lo admita es crear los componentes de back-end necesarios, como un motor de depuración (de). Es donde [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] entra en.  
  
 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Incluye una referencia completa a todos los [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] elementos necesarios para crear un nuevo de. Además, hay ejemplos y tutoriales que le ayudarán a empezar.  
  
 Para obtener un ejemplo de un extremo a otro de un sistema de proyectos de lenguaje con compatibilidad para la depuración, consulte el [ejemplo de IronPython](https://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 En las secciones siguientes se describe cómo extender el depurador mediante el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
## <a name="in-this-section"></a>En esta sección  
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Describe [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] las ofertas de depuración y cómo instalar el SDK.  
  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Documenta el proceso personalizado DE, desde preparar el programa para un DE para desasociar DE.  
  
 [Escritura de un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Explica si debe escribir un evaluador de expresiones.  
  
 [Elección de una estrategia de implementación del motor de depuración](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Describe cómo implementar su DE.  
  
 [Referencia](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Documenta la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] API de depuración.  
  
 [Muestras](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Contiene vínculos a un ejemplo del evaluador de expresiones Common Language Runtime y un ejemplo del motor de depuración.
