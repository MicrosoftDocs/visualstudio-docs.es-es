---
title: Componentes del depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 12f865e7d4c44cfa4002b330ed85ec95f95a8ef9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999011"
---
# <a name="debugger-components"></a>Componentes del depurador
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depurador se implementa como un paquete VSPackage y administra la sesión de depuración completa. La sesión de depuración compone de los siguientes elementos:  
  
- **Depurar el paquete:** El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depurador proporciona la misma interfaz de usuario independientemente de lo que se está depurando.  
  
- **Administrador de depuración de la sesión (SDM):** Proporciona una interfaz de programación coherente para el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depurador para la administración de una variedad de motores de depuración. Se implementa mediante [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
- **Administrador de depuración del proceso (PDM):** Administra todas las instancias de ejecución de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], una lista de todos los programas que pueden o que se están depurando. Se implementa mediante [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
- **Depurar el motor (DE):** Es responsable de supervisar un programa que se está depurando, comunica el estado del programa en ejecución en el SDM y el PDM e interactuar con el evaluador de expresiones y el proveedor de símbolos para proporcionar análisis en tiempo real del estado de memoria de un programa y variables. Se implementa mediante [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (para los idiomas que admite) y los proveedores de terceros que va a utilizar su propio tiempo de ejecución.  
  
- **Evaluador de expresiones (EE):** Proporciona compatibilidad para dinámicamente evaluar variables y expresiones suministradas por el usuario cuando un programa se ha detenido en un momento determinado. Se implementa mediante [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (para los idiomas que admite) y los proveedores de terceros que desean admitir en su propio idioma.  
  
- **Proveedor de símbolos (SP):** También se denomina un controlador de símbolos, asigna los símbolos de depuración de un programa a una instancia en ejecución del programa para que se puede proporcionar información significativa (por ejemplo, la depuración de nivel de código fuente y la evaluación de expresiones). Se implementa mediante [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (para Common Language Runtime [CLR] símbolos y la base de datos de programa [PDB] símbolo de formato de archivo) y por los proveedores de terceros que tienen su propio método propietaria de almacenar información de depuración.  
  
  El siguiente diagrama muestra la relación entre estos elementos del depurador de Visual Studio.  
  
  ![Introducción a los componentes de depuración](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>En esta sección  
 [Depuración de paquete](../../extensibility/debugger/debug-package.md)  
 Describe el paquete de depuración, que se ejecuta en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] de shell y se encarga de toda la interfaz de usuario.  
  
 [Administrador de depuración del proceso](../../extensibility/debugger/process-debug-manager.md)  
 Proporciona información general de las características de PDM, que es el Administrador de los procesos que se pueden depurar.  
  
 [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md)  
 Define el SDM, que proporciona una vista unificada de la sesión de depuración para el IDE. El SDM administra la DE.  
  
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)  
 Documenta los servicios de depuración que proporciona la DE.  
  
 [Modos de funcionamiento](../../extensibility/debugger/operational-modes.md)  
 Proporciona información general de los tres modos en que puede funcionar el IDE: modo de diseño, modo de ejecución y modo de interrupción. También se describen los mecanismos de transición.  
  
 [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md)  
 Explica el propósito de lo EE en tiempo de ejecución.  
  
 [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md)  
 Describe cómo hacerlo, en la implementación, el proveedor de símbolos se evalúa como variables y expresiones.  
  
 [Visualizador de tipo y visor personalizado](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Explica qué son un visualizador de tipo y el visor personalizado y qué función que desempeña el evaluador de expresiones en que admiten ambos.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)  
 Describe los principales conceptos de arquitectura de depuración.  
  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica el funcionamiento de la DE simultáneamente dentro de código, documentación y contextos de evaluación de expresión. Se describen para cada uno de los tres contextos, la ubicación, posición o evaluación pertinente a él.  
  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)  
 Contiene vínculos a diversas tareas de depuración, como iniciar un programa y evaluar expresiones.  
  
## <a name="see-also"></a>Vea también  
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
