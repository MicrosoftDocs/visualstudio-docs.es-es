---
title: Configuración de proyecto para administrar la implementación | Microsoft Docs
description: Obtenga información sobre la implementación en la ubicación esperada para la depuración e instalación, y las dos formas en que Visual Studio es compatible con proyectos que admiten la implementación de.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 5c322e320e193acd25a011cc85173c1c80e2d29d
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877993"
---
# <a name="project-configuration-for-managing-deployment"></a>Configuración del proyecto para administrar la implementación
La implementación es el acto de mover físicamente los elementos de salida de un proceso de compilación a la ubicación esperada para la depuración y la instalación. Por ejemplo, una aplicación web podría estar compilada en un equipo local y, a continuación, colocarse en el servidor.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] admite dos maneras en que los proyectos pueden estar implicados en la implementación:

- Como asunto del proceso de implementación.

- Como administrador del proceso de implementación.

  Antes de implementar las soluciones, primero debe agregar un proyecto de implementación para configurar las opciones de implementación. Si el proyecto de implementación aún no existe, se le pregunta si desea crear uno al seleccionar **implementar solución** en el menú **compilar** o hacer clic con el botón secundario en la solución. Al hacer clic en **sí** , se abre el cuadro de diálogo **Agregar nuevo proyecto** con el proyecto del **Asistente para implementar remoto** seleccionado.

  El Asistente para la implementación remota le pide el tipo de aplicación (Windows o Web), los grupos de resultados del proyecto que se van a incluir, los archivos adicionales que desee incluir y el equipo remoto en el que desea realizar la implementación. La última página del asistente muestra un resumen de las opciones seleccionadas.

  Los proyectos que están sujetos a un proceso de implementación producen elementos de salida que se deben pasar a un entorno alternativo. Estos elementos de salida se describen como parámetros de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> interfaz, cuyo propósito principal es permitir que los proyectos agrupen salidas. Para obtener más información sobre la implementación de `IVsProjectCfg2` , vea [configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md).

  Los proyectos de implementación, que administran el proceso de implementación, habilitan el comando implementar y responden cuando se selecciona este comando. Los proyectos de implementación implementan la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaz para realizar la implementación y realizan llamadas a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> interfaz para notificar los eventos de estado de implementación.

  Las configuraciones pueden especificar las dependencias que afectan a las operaciones de compilación o implementación. Las dependencias de compilación o implementación son proyectos que deben compilarse o implementarse antes o después de que se compilen o implementen las propias configuraciones. Las dependencias de compilación entre proyectos se describen con la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> interfaz e implementan las dependencias con la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfaz. Para obtener más información, vea [configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Consulte también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)
- [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)
