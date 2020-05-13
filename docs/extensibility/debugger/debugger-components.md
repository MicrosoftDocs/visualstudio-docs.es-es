---
title: Componentes del depurador (Debugger Components) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03c400fd03c5ee0f2629e9f436b65f53f8f2ac8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739012"
---
# <a name="debugger-components"></a>Componentes del depurador
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador se implementa como un VSPackage y administra toda la sesión de depuración. La sesión de depuración consta de los siguientes elementos:

- **Paquete de depuración:** El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador proporciona la misma interfaz de usuario independientemente de lo que se está depurando.

- **Administrador de depuración de sesión (SDM):** Proporciona una interfaz de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] programación coherente al depurador para la administración de una variedad de motores de depuración. Se implementa por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- **Administrador de depuración de procesos (PDM):** Administra, para todas las [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]instancias en ejecución de , una lista de todos los programas que pueden ser o se están depurando. Se implementa por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- **Motor de depuración (DE):** Es responsable de supervisar un programa que se está depurando, comunicar el estado del programa en ejecución al SDM y PDM e interactuar con el evaluador de expresiones y el proveedor de símbolos para proporcionar un análisis en tiempo real del estado de la memoria y las variables de un programa. Se implementa por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (para los idiomas que admite) y proveedores de terceros que desean admitir su propio tiempo de ejecución.

- **Evaluador de expresiones (EE):** Proporciona compatibilidad con la evaluación dinámica de variables y expresiones proporcionadas por el usuario cuando un programa se ha detenido en un punto determinado. Se implementa por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (para los idiomas que admite) y proveedores de terceros que quieren admitir sus propios idiomas.

- **Proveedor de símbolos (SP):** También denominado controlador de símbolos, asigna los símbolos de depuración de un programa a una instancia en ejecución del programa para que se pueda proporcionar información significativa (como la depuración de nivel de código fuente y la evaluación de expresiones). Se implementa mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (para los símbolos de Common Language Runtime [CLR] y el formato de archivo de símbolos de Base de datos de programa [PDB]) y por proveedores externos que tienen su propio método propietario de almacenamiento de información de depuración.

  En el diagrama siguiente se muestra la relación entre estos elementos del depurador de Visual Studio.

  ![Información general sobre componentes de depuración](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>En esta sección
 [Paquete de depuración](../../extensibility/debugger/debug-package.md) Describe el paquete de depuración, que se ejecuta en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell y controla toda la interfaz de usuario.

 [Administrador de depuración de procesos](../../extensibility/debugger/process-debug-manager.md) Proporciona una visión general de las características de PDM, que es el administrador de los procesos que se pueden depurar.

 [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md) Define el SDM, que proporciona una vista unificada de la sesión de depuración al IDE. El SDM administra el DE.

 [Motor de depuración](../../extensibility/debugger/debug-engine.md) Documenta los servicios de depuración que proporciona la DE.

 [Modos operativos](../../extensibility/debugger/operational-modes.md) Proporciona una visión general de los tres modos en los que el IDE puede operar: modo de diseño, modo de ejecución y modo de interrupción. También se discuten los mecanismos de transición.

 [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md) Explica el propósito de EE en tiempo de ejecución.

 [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md) Describe cómo, en la implementación, el proveedor de símbolos evalúa variables y expresiones.

 [Visualizador de tipos y visor personalizado](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Describe qué son un visualizador de tipos y un visor personalizado y qué función desempeña el evaluador de expresiones al admitir ambos.

## <a name="related-sections"></a>Secciones relacionadas
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md) Describe los principales conceptos arquitectónicos de depuración.

 [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md) Explica cómo funciona la DE simultáneamente dentro de los contextos de evaluación de código, documentación y expresión. Describe, para cada uno de los tres contextos, la ubicación, la posición o la evaluación relevantes para ella.

 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md) Contiene vínculos a varias tareas de depuración, como iniciar un programa y evaluar expresiones.

## <a name="see-also"></a>Vea también
- [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
