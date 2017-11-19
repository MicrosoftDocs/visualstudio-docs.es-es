---
title: "Configuración de proyecto para administrar la implementación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 87098c362e5b37690e2ab3116ffca431d58f129d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="project-configuration-for-managing-deployment"></a>Configuración del proyecto para administrar la implementación
Implementación es el acto de mover físicamente los elementos de salida de un proceso de compilación a la ubicación esperada para la depuración y la instalación. Por ejemplo, una aplicación Web se podría basada en un equipo local y, a continuación, se coloca en el servidor.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]admite dos formas de proyectan puede estar implicado en la implementación:  
  
-   Como el sujeto del proceso de implementación.  
  
-   Como el administrador del proceso de implementación.  
  
 Para pueden implementar las soluciones, primero debe agregar un proyecto de implementación para configurar las opciones de implementación. Si el proyecto de implementación no existe, se le preguntará si desea crear una cuando se selecciona **implementar solución** desde el **generar** menú o menú contextual de la solución. Haga clic en **Sí** abre el **Agregar nuevo proyecto** cuadro de diálogo con el **Asistente para implementación remota** proyecto seleccionado.  
  
 El Asistente para implementación remota en el que se le pide que para el tipo de aplicación (Windows o Web), los grupos de salida del proyecto para incluir, los archivos adicionales que van a incluir y el equipo remoto que desea implementar en. La última página del asistente muestra un resumen de las opciones seleccionadas.  
  
 Los proyectos que son el asunto de un proceso de implementación generan elementos de salida que se deben mover a un entorno alternativo. Estos resultados se describen los elementos como parámetros para el <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> interfaz, cuya principal finalidad deben permitir que los proyectos a las salidas de grupo. Para obtener más información sobre la implementación de `IVsProjectCfg2`, consulte [configuración del proyecto para la salida de](../../extensibility/internals/project-configuration-for-output.md).  
  
 Proyectos de implementación, que administración el proceso de implementación, habilitan el comando implementar y responden cuando se selecciona este comando. Implementan proyectos de implementación de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfaz para realizar la implementación y realizar llamadas a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> interfaz al informe implementar eventos de estado.  
  
 Configuraciones pueden especificar las dependencias que afectan a sus operaciones de compilación o implementación. Compilar o implementar las dependencias son proyectos que deben estar integrados o implementados antes o después de que se generan o se implementan las configuraciones por sí mismos. Se describen las dependencias de compilación entre proyectos con la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> interfaz e implementar las dependencias con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfaz. Para obtener más información, consulte [configuración del proyecto para compilar](../../extensibility/internals/project-configuration-for-building.md).  
  
## <a name="see-also"></a>Vea también  
 [Administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md)   
 [Configuración del proyecto para una compilación](../../extensibility/internals/project-configuration-for-building.md)   
 [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)