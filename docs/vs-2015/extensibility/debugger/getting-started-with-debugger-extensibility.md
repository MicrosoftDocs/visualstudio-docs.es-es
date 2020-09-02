---
title: Introducción con extensibilidad del depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1c616c7cf8ed90ec3d76046892167b9b742a1b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152700"
---
# <a name="getting-started-with-debugger-extensibility"></a>Introducción a la extensibilidad del depurador
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Proporciona la información que debe tener para crear y personalizar los componentes del depurador usados para depurar programas desde dentro del [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entorno de.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] la depuración ha agregado mejoras derivadas de las amplias pruebas de uso realizadas en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depuradores anteriores. Puede usar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] la depuración para recorrer paso a paso una aplicación de varios lenguajes, o puede implementar la edición inmediata de variables durante la depuración de aplicaciones y soluciones de varios lenguajes.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] la depuración se ejecuta fuera de proceso con el programa que se está depurando y, por lo tanto, es menos intrusivo en el espacio de proceso de la aplicación. Por consiguiente, es más fácil escribir componentes que interactúen con el depurador sin que ello afecte al programa de depuración.  
  
 Para usar mejor el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , debe estar familiarizado con lo siguiente:  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Entorno de desarrollo integrado (IDE)  
  
- Lenguaje de programación de C++  
  
- COM ATL  
  
## <a name="in-this-section"></a>En esta sección  
 [Guía básica para ampliar el depurador](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Describe el proceso de implementación de la depuración en el producto, dependiendo del compilador y de su salida.  
  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)  
 Proporciona información general sobre los [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] componentes de depuración, que incluyen el motor de depuración (de), el evaluador de expresiones (EE) y el controlador de símbolos (SH).  
  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)  
 Describe los conceptos principales de la arquitectura de depuración.  
  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica cómo el motor DE depuración (DE) funciona simultáneamente dentro del código, la documentación y los contextos de evaluación de expresiones. Describe, para cada uno de los tres contextos, la ubicación, la posición o la evaluación relevantes para él.  
  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)  
 Contiene vínculos a diversas tareas de depuración, como el inicio de un programa y la evaluación de expresiones.
