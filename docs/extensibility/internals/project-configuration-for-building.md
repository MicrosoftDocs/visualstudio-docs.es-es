---
title: Configuración del proyecto para compilar | Microsoft Docs
description: Obtenga información sobre cómo se administra una lista de configuraciones de soluciones para una solución determinada mediante el cuadro de diálogo Configuraciones de solución en un nuevo tipo de proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf98698d3527220c4bc25cdf36132f0088ae4ea7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899935"
---
# <a name="project-configuration-for-building"></a>Configuración del proyecto para la compilación
La lista de configuraciones de soluciones para una solución determinada se administra mediante el cuadro de diálogo Configuraciones de solución .

 Un usuario puede crear configuraciones de solución adicionales, cada una con su propio nombre único. Cuando el usuario crea una nueva configuración de solución, el IDE tiene como valor predeterminado el nombre de configuración correspondiente en los proyectos o Depurar si no existe ningún nombre correspondiente. El usuario puede cambiar la selección para cumplir requisitos específicos si es necesario. La única excepción a este comportamiento es cuando el proyecto admite una configuración que coincide con el nombre de la nueva configuración de la solución. Por ejemplo, suponga que una solución contiene Project1 y Project2. Project1 tiene configuraciones de proyecto Debug, Retail y MyConfig1. Project2 tiene configuraciones de proyecto Debug, Retail y MyConfig2.

 Si el usuario crea una nueva configuración de solución denominada MyConfig2, Project1 enlaza su configuración de depuración a la configuración de la solución de forma predeterminada. Project2 también enlaza su configuración MyConfig2 a la configuración de la solución de forma predeterminada.

> [!NOTE]
> El enlace no tiene en cuenta mayúsculas de minúsculas.

 Cuando el usuario selecciona el elemento **Selección** múltiple en la lista desplegable de configuración, el entorno muestra un cuadro de diálogo que proporciona la lista de configuraciones disponibles.

 ![Varias configuraciones](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Varias configuraciones

 Dentro de este cuadro de diálogo, el usuario puede seleccionar una o varias configuraciones. Una vez seleccionados, los valores de propiedad mostrados en el cuadro de diálogo páginas de propiedades reflejan la intersección de valores de las configuraciones seleccionadas.

 Consulte [Configuración de la](../../extensibility/internals/solution-configuration.md) solución para obtener información relacionada con la adición y el cambio de nombre de configuraciones para soluciones y proyectos.

 Las dependencias del proyecto y el orden de compilación son independientes de la configuración de la solución; es decir, solo puede configurar un árbol de dependencias para todos los proyectos de la solución. Al hacer clic con el botón derecho en la solución o el proyecto y seleccionar la opción **Dependencias** del proyecto o **Orden** de compilación del proyecto, se abre el cuadro de diálogo **Dependencias** del proyecto . También se puede abrir desde el **menú** Proyecto.

 ![Dependencias del proyecto](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") Dependencias del proyecto

 Las dependencias del proyecto determinan el orden en que se compilan los proyectos. Use la pestaña Orden de compilación del cuadro de diálogo para ver el orden exacto en el que se compilarán los proyectos de una solución y use la pestaña Dependencias para modificar el orden de compilación.

> [!NOTE]
> El entorno ha agregado proyectos de la lista que tienen activadas sus casillas pero aparecen atenuados debido a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> dependencias explícitas especificadas por las interfaces o y no se pueden <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> cambiar. Por ejemplo, agregar una referencia de proyecto de un proyecto a otro agrega automáticamente una dependencia de compilación que solo se puede [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] quitar eliminando la referencia. Los proyectos cuyas casillas están claras y aparecen atenuadas no se pueden seleccionar porque, al hacerlo, se crearía un bucle de dependencia (por ejemplo, Project1 dependería de Project2 y Project2 dependería de Project1), lo que detendría la compilación.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Los procesos de compilación incluyen las operaciones típicas de compilación y vínculo que se invocan con un único comando Build. También se admiten otros dos procesos de compilación: una operación limpia para eliminar todos los elementos de salida de una compilación anterior y una comprobación actualizada para determinar si ha cambiado un elemento de salida de una configuración.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> Los objetos devuelven un <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> correspondiente (devuelto desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A> ) para administrar sus procesos de compilación. Para notificar el estado de una operación de compilación mientras se está produciendo, las configuraciones hacen llamadas a , una interfaz implementada por el entorno y cualquier otro objeto interesado en eventos de estado <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback> de compilación.

 Una vez creadas, las opciones de configuración se pueden usar para determinar si se pueden ejecutar o no bajo el control del depurador. Las configuraciones se <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> implementan para admitir la depuración.

 Después de implementar las dependencias del proyecto, puede manipular las dependencias mediante programación a través del modelo de automatización. Llame a <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> en el modelo de automatización. No hay interfaces de nivel de API de VSIP disponibles que permitan la manipulación directa de las configuraciones del administrador de compilación de soluciones y sus propiedades.

 Además, puede proporcionar una cuadrícula en la ventana de dependencias del proyecto. Para obtener más información, vea [Cuadrícula de visualización de propiedades.](../../extensibility/internals/properties-display-grid.md)

## <a name="see-also"></a>Consulta también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para administrar la implementación](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)
