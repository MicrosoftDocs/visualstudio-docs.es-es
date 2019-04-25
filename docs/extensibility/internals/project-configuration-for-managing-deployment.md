---
title: Configuración de proyecto para administrar la implementación | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c9bf9dd71007e3a33a217a7ec30b357cd211b00
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629682"
---
# <a name="project-configuration-for-managing-deployment"></a>Configuración del proyecto para administrar la implementación
Implementación es el acto de mover físicamente los elementos de salida de un proceso de compilación a la ubicación esperada para la depuración y la instalación. Por ejemplo, una aplicación Web se podría basada en un equipo local y, a continuación, se coloca en el servidor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite dos formas de proyectan puede estar implicado en la implementación:

- Como el sujeto del proceso de implementación.

- Como el administrador del proceso de implementación.

  Antes de que se pueden implementar soluciones, primero debe agregar un proyecto de implementación para configurar las opciones de implementación. Si el proyecto de implementación no existe, se le pregunte si desea crear uno cuando se selecciona **implementar solución** desde el **compilar** menú o con el botón secundario en la solución. Al hacer clic en **Sí** abre el **Agregar nuevo proyecto** cuadro de diálogo con el **Asistente para implementación remota** proyecto seleccionado.

  El Asistente para implementación remota le pide para el tipo de aplicación (Windows o Web), los grupos de salida del proyecto para incluir, los archivos adicionales que van a incluir y el equipo remoto que desea implementar en. La última página del asistente muestra un resumen de las opciones seleccionadas.

  Los proyectos que son el asunto de un proceso de implementación producen los elementos de salida que se deben mover a un entorno alternativo. Estos resultados se describen los elementos como parámetros para el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> interfaz, cuya principal finalidad if permitir que los proyectos agrupen resultados. Para obtener más información sobre la implementación de `IVsProjectCfg2`, consulte [configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md).

  Proyectos de implementación, que administración el proceso de implementación, habilitan el comando implementar y responden cuando se selecciona este comando. Implementan proyectos de implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaz para realizar la implementación y realizar llamadas a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> eventos de estado de implementación de interfaz al informe.

  Las configuraciones pueden especificar dependencias que afectan a sus operaciones de compilación o implementación. Compilar o implementar las dependencias son proyectos que deben estar creados o implementados antes o después de compilar o implementar las configuraciones a sí mismos. Se describen las dependencias entre proyectos de compilación con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> interfaz e implementar las dependencias con la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfaz. Para obtener más información, consulte [configuración del proyecto para compilar](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Vea también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)
- [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)