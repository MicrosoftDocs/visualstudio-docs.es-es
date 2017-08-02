---
title: "Componentes del depurador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depuración [Visual Studio], componentes"
  - "componentes [Visual Studio SDK], depuración"
  - "[SDK de depuración], componentes de depuración"
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 30
---
# Componentes del depurador
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Implementan como VSPackage y administra el depurador de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a la sesión completa de depuración.  La sesión de depuración está formado por los siguientes elementos:  
  
-   **Paquete de depuración:** el depurador de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona la misma interfaz de usuario no importa qué se está depurando.  
  
-   **Administrador \(SDM\) de depuración de sesión:** Proporciona una interfaz de programación coherente al depurador de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para la administración de varios motores de depuración.  Se implementa mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **Administrador \(PDM\) de depuración:** Administra, para todas las instancias de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], una lista de todos los programas que pueden ser o que se están depurando.  Se implementa mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **Motor \(DE\) de depuración:** Es responsable de supervisar un programa que se está depurando, comunicándose al estado del programa en ejecución al SDM y el PDM, y interactuando con el evaluador de expresiones y el proveedor del token para proporcionar el análisis en tiempo real del estado de la memoria y variables de un programa.  Se implementa mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(para los lenguajes que admite\) y los proveedores de terceros que deseen admitir su propio runtime.  
  
-   **Evaluador \(EE\) de expresiones:** Proporciona compatibilidad para las variables y expresiones dinámicamente de evaluación proporcionadas por el usuario cuando un programa se ha detenido en un punto determinado.  Se implementa mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(para los lenguajes que admite\) y los proveedores de terceros que desean para admitir sus propios lenguajes.  
  
-   **Proveedor \(SP\) de token:** También denominado un controlador de símbolos, asigna los símbolos de depuración de un programa a una instancia en ejecución del programa para poder proporcionar información significativa \(como la depuración de origen\-código\-nivel y la evaluación de la expresión\).  Se implementa mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(para los símbolos de Common Language Runtime \[CLR\] y el formato de archivo de símbolos de la base de datos de programa \(PDB \[\]\) y por los proveedores de terceros que tienen su propio método propietario de almacenar la información de depuración.  
  
 El siguiente diagrama muestra la relación entre estos elementos del depurador de Visual Studio.  
  
 ![Información general sobre componentes de depuración](~/docs/extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## En esta sección  
 [Depurar paquete](../../extensibility/debugger/debug-package.md)  
 Describe el paquete de depuración, que se ejecuta en el shell de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y administra toda la interfaz de usuario.  
  
 [Administrador de depuración del proceso](../../extensibility/debugger/process-debug-manager.md)  
 Proporciona información general sobre las características de PDM, que es el administrador de los procesos que pueden ser depurados.  
  
 [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md)  
 Define el SDM, que proporciona una vista unificada la sesión de depuración al IDE.  El SDM administra el OF.  
  
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)  
 Documenta los servicios de depuración que el OF proporciona.  
  
 [Modos de funcionamiento](../../extensibility/debugger/operational-modes.md)  
 Proporciona información general sobre los tres modos en los que el IDE puede trabajar: modo de diseño, modo de ejecución, y el modo de interrupción.  Los mecanismos de transición también se analizan.  
  
 [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md)  
 Explica el propósito de aa en tiempo de ejecución.  
  
 [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)  
 Explica cómo, en la implementación, el proveedor del token evalúa variables y expresiones.  
  
 [Visualizador de tipo y el visor personalizado](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Explica qué son un visualizador de tipos y un visor personalizado de y el rol que desempeña el evaluador de expresiones en admitir ambos.  
  
## Secciones relacionadas  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)  
 Describe los conceptos arquitectónicos de depuración principal.  
  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica cómo el OF funciona simultáneamente en el código, de la documentación, y de contextos de la evaluación de la expresión.  Describe, para cada uno de los tres contextos, location, de la posición, o de evaluación relevante para el.  
  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)  
 Contiene vínculos a las diferentes tareas de depuración, como iniciar un programa y evaluación de expresiones.  
  
## Vea también  
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)