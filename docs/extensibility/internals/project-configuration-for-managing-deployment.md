---
title: Configuración del proyecto para administrar la implementación | Microsoft Docs
description: Obtenga información sobre la implementación en la ubicación esperada para la depuración y la instalación, y las dos Visual Studio admite proyectos que admiten la implementación.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3c6077665ccc3bbe5f87b91a1d2fc5636e08539d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899906"
---
# <a name="project-configuration-for-managing-deployment"></a>Configuración del proyecto para administrar la implementación
La implementación es el acto de mover físicamente los elementos de salida de un proceso de compilación a la ubicación esperada para la depuración y la instalación. Por ejemplo, una aplicación web podría estar integrada en un equipo local y, a continuación, colocarse en el servidor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite dos maneras de que los proyectos puedan estar implicados en la implementación:

- Como asunto del proceso de implementación.

- Como administrador del proceso de implementación.

  Para poder implementar soluciones, primero debe agregar un proyecto de implementación para configurar las opciones de implementación. Si el proyecto de implementación aún no existe, se le  pregunta si  desea crear uno al seleccionar Implementar solución en el menú Compilar o hacer clic con el botón derecho en la solución. Al **hacer clic en** Sí, se abre el cuadro de diálogo **Agregar** nuevo proyecto con el proyecto del Asistente **para implementación** remota seleccionado.

  El Asistente para implementación remota le pide el tipo de aplicación (Windows o Web), los grupos de salida del proyecto que se incluirán, los archivos adicionales que quiera incluir y el equipo remoto en el que desea realizar la implementación. La última página del asistente muestra un resumen de las opciones seleccionadas.

  Los proyectos que son objeto de un proceso de implementación generan elementos de salida que se deben mover a un entorno alternativo. Estos elementos de salida se describen como parámetros para la interfaz , cuyo propósito principal es permitir a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> los proyectos agrupar salidas. Para obtener más información relacionada con la implementación de `IVsProjectCfg2` , vea Project Configuration for [Output](../../extensibility/internals/project-configuration-for-output.md).

  Los proyectos de implementación, que administran el proceso de implementación, habilitan el comando Implementar y responden cuando se selecciona este comando. Los proyectos de implementación <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> implementan la interfaz para realizar la implementación y realizar llamadas a la interfaz para notificar eventos de estado <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> de implementación.

  Las configuraciones pueden especificar dependencias que afectan a sus operaciones de compilación o implementación. Las dependencias de compilación o implementación son proyectos que se deben compilar o implementar antes o después de que se compilen o implementen las propias configuraciones. Las dependencias de compilación entre proyectos se describen con <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> la interfaz e implementan dependencias con la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> . Para obtener más información, vea [Project Configuration for Building](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Consulta también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)
- [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)
