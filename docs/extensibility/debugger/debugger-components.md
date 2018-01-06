---
title: Componentes del depurador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1137c8c5c6041b41e8cbdc0e13d43b6188bd1b1b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="debugger-components"></a>Componentes del depurador
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador se implementa como un paquete VSPackage y administra la sesión de depuración completa. La sesión de depuración consta de los siguientes elementos:  
  
-   **Paquete de depuración:** el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador proporciona la misma interfaz de usuario con independencia de lo que se está depurando.  
  
-   **Administrador de sesión de depuración (SDM):** proporciona una interfaz de programación coherente para el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador para la administración de una variedad de motores de depuración. Se implementa mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **Administrador de depuración de procesos (PDM):** administra, para todas las instancias en ejecución de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], una lista de todos los programas que pueden o que se están depurando. Se implementa mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **Depurar motor (Alemania):** es responsable de supervisar un programa que se está depurando, comunicando el estado del programa en ejecución para el SDM y PDM e interactuar con el evaluador de expresiones y el proveedor de símbolos para proporcionar análisis en tiempo real de la estado de memoria y las variables de un programa. Se implementa mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (para los idiomas que admite) y los proveedores de terceros que quieran para admitir su propio tiempo de ejecución.  
  
-   **Evaluador de expresiones (EE):** proporciona compatibilidad para dinámicamente evaluar variables y expresiones suministradas por el usuario cuando un programa se ha detenido en un momento determinado. Se implementa mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (para los idiomas que admite) y los proveedores de terceros que quieran para admitir sus propios lenguajes.  
  
-   **Proveedor de símbolos (SP):** también se denomina un controlador de símbolos, asigna los símbolos de depuración de un programa a una instancia en ejecución del programa para que se puede proporcionar información significativa (por ejemplo, la evaluación de expresión y depuración de nivel de código fuente). Se implementa mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (para Common Language Runtime [CLR] símbolos y la base de datos de programa [PDB] de símbolos de formato de archivo) y por los proveedores de terceros que tienen su propio método propietario de almacenar información de depuración.  
  
 El siguiente diagrama muestra la relación entre estos elementos del depurador de Visual Studio.  
  
 ![Información general sobre componentes de depuración](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>En esta sección  
 [Depuración de paquete](../../extensibility/debugger/debug-package.md)  
 Describe el paquete de depuración, que se ejecuta en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de shell y se encarga de toda la interfaz de usuario.  
  
 [Administrador de depuración del proceso](../../extensibility/debugger/process-debug-manager.md)  
 Proporciona información general de las características de la PDM, que es el Administrador de los procesos que se pueden depurar.  
  
 [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md)  
 Define el SDM, que proporciona una vista unificada de la sesión de depuración para el IDE. El SDM administra la Alemania.  
  
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)  
 Documenta los servicios de depuración que proporciona el Alemania.  
  
 [Modos de funcionamiento](../../extensibility/debugger/operational-modes.md)  
 Proporciona información general de los tres modos en los que puede operar el IDE: modo de diseño, modo de ejecución y el modo de interrupción. También se describen los mecanismos de transición.  
  
 [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md)  
 Explica el propósito de lo EE en tiempo de ejecución.  
  
 [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)  
 Describe cómo hacerlo, en la implementación, el proveedor de símbolos se evalúa como variables y expresiones.  
  
 [Visualizador de tipo y visor personalizado](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Explica qué son un visualizador de tipo y un visor personalizado y qué función que desempeña el evaluador de expresiones de soporte.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)  
 Describe los principales conceptos de arquitectura de depuración.  
  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica el funcionamiento de la DE forma simultánea dentro de código, documentación y los contextos de evaluación de expresión. Describe, para cada uno de los tres contextos, la ubicación, posición o evaluación pertinente a él.  
  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)  
 Contiene vínculos a varias tareas de depuración, como iniciar un programa y la evaluación de expresiones.  
  
## <a name="see-also"></a>Vea también  
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)