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
ms.openlocfilehash: e337e87d162ac59cc6bb45676c1411692dd1a3bb
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675265"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilidad del depurador de Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio incluye a un depurador de código fuente totalmente interactivas, que proporciona una herramienta eficaz y fácil de usar para localizar errores en el programa. El depurador tiene compatibilidad completa con Visual Basic, C#, C/C++ y JavaScript. Sin embargo, con el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], que se disponibles desde el [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453),, pueden admitir otros lenguajes de programación en el depurador con las mismas características enriquecidas.  
  
 El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depurador es el front-end común (es decir, la interfaz de usuario) para los componentes de depuración que son, a su vez, específica del lenguaje que se está depurando. Para nuevos idiomas, todo lo necesario para admitir por los [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depurador consiste en crear los componentes necesarios de back-end, por ejemplo, un motor de depuración (DE). Que es donde el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] entra en juego.  
  
 El [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] incluye una referencia completa a todos los [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] elementos necesarios para crear un DE nuevo. Además, hay ejemplos y tutoriales que le ayudarán a comenzar.  
  
 Para obtener un ejemplo extremo a otro de un sistema de proyectos de lenguaje con compatibilidad con la depuración, vea el [ejemplo de IronPython](https://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 Las secciones siguientes describen cómo ampliar el depurador mediante el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
## <a name="in-this-section"></a>En esta sección  
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Describe qué [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ofertas y cómo instalar el SDK de depuración.  
  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Documenta el proceso DE personalizado, desde la preparación de su programa para un DE para separar la DE.  
  
 [Escritura de un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Explica si debe escribir un evaluador de expresiones.  
  
 [Elección de una estrategia de implementación del motor de depuración](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Describe cómo implementar su DE.  
  
 [Referencia](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Documentos la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] API de depuración.  
  
 [Muestras](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Contiene vínculos a un ejemplo de common language runtime expresión del evaluador de expresiones y un ejemplo de motor de depuración.
