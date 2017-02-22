---
title: "Extensibilidad del depurador de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SDK de depuración, de depuración [Visual Studio]"
  - "SDK de depuración"
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 32
caps.handback.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
---
# Extensibilidad del depurador de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio incluye a un depurador de código fuente totalmente interactivas, proporciona una herramienta eficaz y fácil de usar para localizar errores en el programa. El depurador tiene compatibilidad completa con Visual Basic, C\#, C o C\+\+ y JavaScript. Sin embargo, con el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], que está disponible desde el [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453),, otros lenguajes de programación se admite en el depurador con las mismas características enriquecidas.  
  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador es el front\-end común \(es decir, la interfaz de usuario\) para los componentes de depuración son, a su vez, específica del lenguaje que se está depurando. Para los nuevos idiomas, todo lo necesario para admitir por la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador es crear los componentes necesarios de back\-end, como un motor de depuración \(DE\). Ahí es donde los [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] entra en juego.  
  
 El [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] incluye una referencia completa a todos los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementos necesarios para crear un DE nuevo. Además, hay ejemplos y tutoriales que le ayudarán a comenzar.  
  
 Para obtener un ejemplo de extremo a extremo de un sistema de proyectos de lenguaje con compatibilidad con la depuración, vea la [IronPython sample](http://msdn.microsoft.com/es-es/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 Las secciones siguientes describen cómo extender el depurador mediante el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
## En esta sección  
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Describe qué [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ofertas y cómo instalar el SDK de depuración.  
  
 [Creación de un motor de depuración](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Describe el proceso DE personalizadas, desde la preparación de su programa para una DE para separar la DE.  
  
 [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Explica si se debe escribir un evaluador de expresiones.  
  
 [Elegir una estrategia de implementación del motor de depuración](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Describe cómo implementar la DE.  
  
 [Referencia](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Documentos el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API de depuración.  
  
 [Muestras](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Contiene vínculos a una muestra de evaluador de expresión de tiempo de ejecución lenguaje común y un ejemplo de motor de depuración.