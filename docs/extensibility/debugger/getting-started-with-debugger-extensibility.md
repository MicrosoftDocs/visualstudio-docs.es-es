---
title: Introducción a extensibilidad del depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8db5e9d42036a7e4b5f1726e2771e143395c5820
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833263"
---
# <a name="get-started-with-debugger-extensibility"></a>Empezar a trabajar con la extensibilidad del depurador
El [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] proporciona la información que necesita para crear y personalizar los componentes del depurador para depurar programas desde el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuración ha agregado mejoras que se deriva de la facilidad de uso extenso las pruebas realizadas en anteriores [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuradores. Puede usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuración paso a través de una aplicación de varios idioma, o puede implementar en marcha de edición de las variables durante la depuración de aplicaciones y soluciones de varios idiomas.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración es ejecutada fuera de proceso con el programa que se está depurando y, por tanto, es menos intrusiva en el espacio de proceso de la aplicación. Por lo tanto, es más fácil escribir componentes que interactúan con el depurador sin que afecte a su programa de depuración.  
  
 Mejor forma de usar el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], debe estar familiarizado con los siguientes elementos:  
  
- El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE)  
  
- El lenguaje de programación de C++  
  
- COM DE ATL  
  
## <a name="in-this-section"></a>En esta sección  
 [Guía básica para ampliar el depurador](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Describe el proceso de implementación de depuración en su producto, según el compilador y su salida.  
  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)  
 Proporciona información general sobre el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurar componentes, que se incluyen el motor de depuración (DE), el evaluador de expresiones (EE) y el controlador de símbolos (SH).  
  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)  
 Describe los principales conceptos de arquitectura de depuración.  
  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica cómo el motor de depuración (DE) funciona simultáneamente dentro de código, documentación y contextos de evaluación de expresión. Se describen para cada uno de los tres contextos, la ubicación, posición o evaluación pertinente a él.  
  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)  
 Contiene vínculos a diversas tareas de depuración, como iniciar un programa y evaluar expresiones.