---
title: Configuración del proyecto para la gestión de la implementación Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62f7bf6535a89e46799ade88fe8976974b3019c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706711"
---
# <a name="project-configuration-for-managing-deployment"></a>Configuración del proyecto para administrar la implementación
La implementación es el acto de mover físicamente los elementos de salida de un proceso de compilación a la ubicación esperada para la depuración y la instalación. Por ejemplo, una aplicación web puede compilarse en un equipo local y, a continuación, colocarse en el servidor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]admite dos formas en que los proyectos pueden participar en la implementación:

- Como el tema del proceso de implementación.

- Como administrador del proceso de implementación.

  Antes de implementar soluciones, primero debe agregar un proyecto de implementación para configurar las opciones de implementación. Si el proyecto de implementación aún no existe, se le preguntará si desea crear uno al seleccionar **Implementar solución** en el menú **Compilar** o hacer clic con el botón secundario en la solución. Al hacer clic en **Sí,** se abre el cuadro de diálogo **Agregar nuevo proyecto** con el proyecto Asistente para **implementación remota** seleccionado.

  El Asistente para implementación remota le pide el tipo de aplicación (Windows o Web), los grupos de salida del proyecto que se van a incluir, los archivos adicionales que desea incluir y el equipo remoto en el que desea implementar. La última página del asistente muestra un resumen de las opciones seleccionadas.

  Los proyectos que son objeto de un proceso de implementación producen elementos de salida que se deben mover a un entorno alternativo. Estos elementos de salida <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> se describen como parámetros para la interfaz, cuyo propósito principal si permitir que los proyectos agrupen las salidas. Para obtener más información sobre `IVsProjectCfg2`la implementación de , vea Configuración del [proyecto para salida](../../extensibility/internals/project-configuration-for-output.md).

  Los proyectos de implementación, que administran el proceso de implementación, habilitan el comando Deploy y responden cuando se selecciona este comando. Los proyectos <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> de implementación implementan la interfaz para realizar la implementación y realizar llamadas a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> interfaz para informar de los eventos de estado de implementación.

  Las configuraciones pueden especificar dependencias que afectan a sus operaciones de compilación o implementación. Las dependencias de compilación o implementación son proyectos que deben compilarse o implementarse antes o después de que se compilen o implementen las propias configuraciones. Las dependencias de compilación <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> entre proyectos se describen con la interfaz e implementan dependencias con la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfaz. Para obtener más información, consulte [Configuración del proyecto para compilar](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Vea también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)
- [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)
