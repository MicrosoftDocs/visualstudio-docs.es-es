---
title: Componentes del depurador | Microsoft Docs
description: Obtenga información sobre los elementos que forma una sesión de depuración, administrada por el depurador de Visual Studio, implementada como un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c246bc00ee4f6fcead8404b3174da39f7b5ca2d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903988"
---
# <a name="debugger-components"></a>Componentes del depurador
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador se implementa como un VSPackage y administra toda la sesión de depuración. La sesión de depuración consta de los siguientes elementos:

- **Paquete de depuración:** El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador proporciona la misma interfaz de usuario independientemente de lo que se esté depurando.

- **Administrador de depuración de sesión (SDM):** Proporciona una interfaz de programación coherente al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador para la administración de una variedad de motores de depuración. Se implementa mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- **Administrador de depuración de procesos (DM):** Administra, para todas las instancias en ejecución de , una lista de todos los programas que se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pueden depurar o se están depurando. Se implementa mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- **Motor de depuración (DE):** Es responsable de supervisar un programa que se está depurando, comunicar el estado del programa en ejecución al SDM y al SERVICIO de administración de aplicaciones e interactuar con el evaluador de expresiones y el proveedor de símbolos para proporcionar análisis en tiempo real del estado de la memoria y las variables de un programa. Lo implementan (para los idiomas que admite) y proveedores de terceros que desean admitir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] su propio tiempo de ejecución.

- **Evaluador de expresiones (EE):** Proporciona compatibilidad para evaluar dinámicamente variables y expresiones proporcionadas por el usuario cuando se ha detenido un programa en un momento determinado. Lo implementan (para los idiomas que admite) y proveedores de terceros que desean admitir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sus propios idiomas.

- **Proveedor de símbolos (SP):** También denominado controlador de símbolos, asigna los símbolos de depuración de un programa a una instancia en ejecución del programa para que se pueda proporcionar información significativa (como la depuración de nivel de código fuente y la evaluación de expresiones). Se implementa mediante (para los símbolos de Common Language Runtime [CLR] y el formato de archivo de símbolos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] program DataBase [PDB]) y por proveedores de terceros que tienen su propio método propietario para almacenar información de depuración.

  En el diagrama siguiente se muestra la relación entre estos elementos del Visual Studio depurador.

  ![Información general sobre componentes de depuración](../../extensibility/debugger/media/dbugcompovrview.gif "DComposiciónCompOvrview")

## <a name="in-this-section"></a>En esta sección
 [Paquete de depuración](../../extensibility/debugger/debug-package.md) Describe el paquete de depuración, que se ejecuta en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell y controla toda la interfaz de usuario.

 [Administrador de depuración de procesos](../../extensibility/debugger/process-debug-manager.md) Proporciona información general sobre las características de LAN, que es el administrador de los procesos que se pueden depurar.

 [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md) Define el SDM, que proporciona una vista unificada de la sesión de depuración para el IDE. El SDM administra el DE.

 [Motor de depuración](../../extensibility/debugger/debug-engine.md) Documenta los servicios de depuración que proporciona el DE.

 [Modos operativos](../../extensibility/debugger/operational-modes.md) Proporciona información general de los tres modos en los que el IDE puede funcionar: modo de diseño, modo de ejecución y modo de interrupción. También se analizan los mecanismos de transición.

 [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md) Explica el propósito del EE en tiempo de ejecución.

 [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md) Describe cómo, en la implementación, el proveedor de símbolos evalúa variables y expresiones.

 [Visualizador de tipos y visor personalizado](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Describe qué son un visualizador de tipos y un visor personalizado y qué rol desempeña el evaluador de expresiones para admitir ambos.

## <a name="related-sections"></a>Secciones relacionadas
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md) Se describen los principales conceptos de la arquitectura de depuración.

 [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md) Se explica cómo funciona el motor de depuración simultáneamente dentro de los contextos de código, documentación y evaluación de expresiones. Para cada uno de los tres contextos, se describen la ubicación, la posición o la evaluación correspondientes.

 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md) Contiene vínculos a varias tareas de depuración, como iniciar un programa y evaluar expresiones.

## <a name="see-also"></a>Consulte también
- [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
