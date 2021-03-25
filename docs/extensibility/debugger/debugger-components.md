---
title: Componentes del depurador | Microsoft Docs
description: Obtenga información sobre los elementos que componen una sesión de depuración, que se administra mediante el depurador de Visual Studio, que se implementa como un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: b7c558d20d24acd65ece4c4df43eb8f474c20447
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094957"
---
# <a name="debugger-components"></a>Componentes del depurador
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador se implementa como un VSPackage y administra la sesión de depuración completa. La sesión de depuración consta de los siguientes elementos:

- **Depurar paquete:** El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador proporciona la misma interfaz de usuario, independientemente de lo que se esté depurando.

- **Administrador de depuración de sesión (SDM):** Proporciona una interfaz de programación coherente al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurador para la administración de diversos motores de depuración. Lo implementa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- **Process Debug Manager (PDM):** Administra, para todas las instancias en ejecución de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , una lista de todos los programas que se pueden depurar o. Lo implementa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- **Motor de depuración (de):** Es responsable de supervisar un programa que se está depurando, comunicando el estado del programa en ejecución con el SDM y el PDM e interactuando con el evaluador de expresiones y el proveedor de símbolos para proporcionar análisis en tiempo real del estado de la memoria y las variables de un programa. Lo implementa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (para los lenguajes que admite) y proveedores de terceros que desean admitir su propio tiempo de ejecución.

- **Evaluador de expresiones (EE):** Proporciona compatibilidad para evaluar dinámicamente las variables y expresiones proporcionadas por el usuario cuando se ha detenido un programa en un punto determinado. Lo implementa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (para los lenguajes que admite) y proveedores de terceros que desean admitir sus propios idiomas.

- **Proveedor de símbolos (SP):** También se denomina controlador de símbolos, asigna los símbolos de depuración de un programa a una instancia en ejecución del programa para que se pueda proporcionar información significativa (como la depuración de nivel de código fuente y la evaluación de expresiones). Lo implementa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (para los símbolos de Common Language Runtime [CLR] y el formato de archivo de símbolos de la base de datos de programa [PDB]) y los proveedores de terceros que tienen su propio método de almacenamiento de la información de depuración.

  En el diagrama siguiente se muestra la relación entre estos elementos del depurador de Visual Studio.

  ![Información general sobre componentes de depuración](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>En esta sección
 [Depurar paquete](../../extensibility/debugger/debug-package.md) Describe el paquete de depuración, que se ejecuta en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell y controla toda la interfaz de usuario.

 [Procesar el administrador de depuración](../../extensibility/debugger/process-debug-manager.md) Proporciona información general sobre las características de PDM, que es el administrador de los procesos que se pueden depurar.

 [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md) Define el SDM, que proporciona una vista unificada de la sesión de depuración al IDE. El SDM administra el DE.

 [Motor de depuración](../../extensibility/debugger/debug-engine.md) Documenta los servicios de depuración que proporciona.

 [Modos operativos](../../extensibility/debugger/operational-modes.md) Proporciona información general de los tres modos en los que el IDE puede operar: el modo de diseño, el modo de ejecución y el modo de interrupción. También se describen los mecanismos de transición.

 [Evaluador de expresiones](../../extensibility/debugger/expression-evaluator.md) Explica el propósito de EE en tiempo de ejecución.

 [Proveedor de símbolos](../../extensibility/debugger/symbol-provider.md) Describe cómo, en la implementación, el proveedor de símbolos evalúa variables y expresiones.

 [Visualizador de tipos y visor personalizado](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Describe lo que son un visualizador de tipos y un visor personalizado y el rol que desempeña el evaluador de expresiones para admitir ambos.

## <a name="related-sections"></a>Secciones relacionadas
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md) Se describen los principales conceptos de la arquitectura de depuración.

 [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md) Se explica cómo funciona el motor de depuración simultáneamente dentro de los contextos de código, documentación y evaluación de expresiones. Para cada uno de los tres contextos, se describen la ubicación, la posición o la evaluación correspondientes.

 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md) Contiene vínculos a diversas tareas de depuración, como el inicio de un programa y la evaluación de expresiones.

## <a name="see-also"></a>Consulte también
- [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
