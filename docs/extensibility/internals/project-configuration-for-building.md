---
title: Configuración del proyecto para la construcción de edificios Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdd084053e06206a99298b234b4d51c8504119a2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706726"
---
# <a name="project-configuration-for-building"></a>Configuración del proyecto para la compilación
La lista de configuraciones de solución para una solución determinada se administra mediante el cuadro de diálogo Configuraciones de solución.

 Un usuario puede crear configuraciones de solución adicionales, cada una con su propio nombre único. Cuando el usuario crea una nueva configuración de solución, el IDE tiene como valor predeterminado el nombre de configuración correspondiente en los proyectos o Depurar si no existe ningún nombre correspondiente. El usuario puede cambiar la selección para cumplir requisitos específicos si es necesario. La única excepción a este comportamiento es cuando el proyecto admite una configuración que coincide con el nombre de la nueva configuración de la solución. Por ejemplo, supongamos que una solución contiene Project1 y Project2. Project1 tiene configuraciones de proyecto Debug, Retail y MyConfig1. Project2 tiene configuraciones de proyecto Debug, Retail y MyConfig2.

 Si el usuario crea una nueva configuración de solución denominada MyConfig2, Project1 enlaza su configuración de depuración a la configuración de la solución de forma predeterminada. Project2 también enlaza su configuración MyConfig2 a la configuración de la solución de forma predeterminada.

> [!NOTE]
> El enlace no distingue mayúsculas de minúsculas.

 Cuando el usuario selecciona el elemento **Selección múltiple** en la lista desplegable de configuración, el entorno muestra un cuadro de diálogo que proporciona la lista de configuraciones disponibles.

 ![Múltiples configuraciones](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Múltiples configuraciones

 Dentro de este cuadro de diálogo, el usuario puede seleccionar una o varias configuraciones. Una vez seleccionado, los valores de propiedad que se muestran en el cuadro de diálogo de páginas de propiedades reflejan la intersección de valores para las configuraciones seleccionadas.

 Consulte Configuración de la [solución](../../extensibility/internals/solution-configuration.md) para obtener información relacionada con la adición y el cambio de nombre de las configuraciones de soluciones y proyectos.

 Las dependencias de proyecto y el orden de compilación son independientes de la configuración de la solución: es decir, solo puede configurar un árbol de dependencias para todos los proyectos de la solución. Al hacer clic con el botón derecho en la solución o proyecto y seleccionar la opción **Dependencias** del proyecto o Orden de **compilación** de proyecto, se abre el cuadro de diálogo Dependencias del **proyecto.** También se puede abrir desde el menú **Proyecto.**

 ![Dependencias del proyecto](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") Dependencias del proyecto

 Las dependencias del proyecto determinan el orden en que se compilan los proyectos. Use la pestaña Orden de compilación del cuadro de diálogo para ver el orden exacto en el que se compilarán los proyectos de una solución y use la pestaña Dependencias para modificar el orden de compilación.

> [!NOTE]
> Los proyectos de la lista que tienen sus casillas de verificación seleccionadas pero <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> aparecen <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> atenuadas se han agregado por el entorno debido a las dependencias explícitas especificadas por las interfaces o y no se pueden cambiar. Por ejemplo, al agregar [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] una referencia de proyecto de un proyecto a otro proyecto, se agrega automáticamente una dependencia de compilación que solo se puede quitar eliminando la referencia. Los proyectos cuyas casillas de verificación están desactivadas y aparecen atenuadas no se pueden seleccionar porque al hacerlo se crearía un bucle de dependencia (por ejemplo, Project1 dependería de Project2 y Project2 dependería de Project1), lo que detendría la compilación.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]los procesos de compilación incluyen las operaciones de compilación y vínculo típicas que se invocan con un único comando Build. También se pueden admitir otros dos procesos de compilación: una operación limpia para eliminar todos los elementos de salida de una compilación anterior y una comprobación actualizada para determinar si un elemento de salida de una configuración ha cambiado.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>objetos devuelven un correspondiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (devuelta desde <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) para administrar sus procesos de compilación. Para informar del estado de una operación de compilación <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>mientras se está produciendo, las configuraciones realizan llamadas a , una interfaz implementada por el entorno y cualquier otro objeto interesado en eventos de estado de compilación.

 Una vez compiladas, los valores de configuración se pueden usar para determinar si se pueden ejecutar o no bajo el control del depurador. Las configuraciones se implementan <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> para admitir la depuración.

 Después de implementar las dependencias del proyecto, puede manipular mediante programación las dependencias a través del modelo de automatización. Llame <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> al modelo de automatización. No hay interfaces de nivel de API de VSIP disponibles que permitan la manipulación directa de las configuraciones del administrador de compilación de soluciones y sus propiedades.

 Además, puede proporcionar una cuadrícula en la ventana de dependencias del proyecto. Para obtener más información, consulte Cuadrícula de [visualización de propiedades](../../extensibility/internals/properties-display-grid.md).

## <a name="see-also"></a>Vea también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para administrar la implementación](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)
