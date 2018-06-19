---
title: Extensibilidad del depurador de Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e5bb01c093fda068dfbc7dfa705914a8bdef4d2b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127075"
---
# <a name="visual-studio-debugger-extensibility"></a>Extensibilidad del depurador de Visual Studio
Visual Studio incluye a un depurador de código fuente totalmente interactivo, proporciona una herramienta eficaz y fácil de usar para realizar un seguimiento de errores en el programa. El depurador tiene compatibilidad completa con Visual Basic, C#, C/C++ y JavaScript. Sin embargo, con el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], es decir disponibles desde el [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453), otros lenguajes de programación pueden admitirse en el depurador con las mismas características enriquecidas.  
  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador es el front-end común (es decir, la interfaz de usuario) para los componentes de depuración que son, a su vez, específica del lenguaje que se está depurando. Para nuevos idiomas, todo lo que es necesario para admitir por los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador consiste en crear los componentes necesarios de back-end, por ejemplo, un motor de depuración (Alemania). Ahí es donde el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] entra en juego.  
  
 El [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] incluye una referencia completa a todos los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementos necesarios para crear un nuevo Alemania. Además, hay ejemplos y tutoriales que le ayudarán a empezar.  
  
 Para obtener un ejemplo de extremo a extremo de un sistema de proyecto de lenguaje con compatibilidad con la depuración, vea el [ejemplo de IronPython](http://msdn.microsoft.com/en-us/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 Las secciones siguientes describen cómo ampliar el depurador mediante el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="in-this-section"></a>En esta sección  
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Describe qué [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ofertas y cómo instalar el SDK de depuración.  
  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Documenta el proceso personalizado de Alemania, desde la preparación del programa para un Alemania para separar el Alemania.  
  
 [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Explica si se debe escribir un evaluador de expresiones.  
  
 [Elección de una estrategia de implementación del motor de depuración](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Describe cómo implementar su Alemania.  
  
 [Referencia](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Documentos la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API de depuración.  
  
 [Ejemplos](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Contiene vínculos a un ejemplo de evaluador expresión de common language runtime y un ejemplo de motor de depuración.
