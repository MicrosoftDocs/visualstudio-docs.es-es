---
title: Configuración del proyecto para compilar | Microsoft Docs
description: Obtenga información sobre cómo se administra una lista de configuraciones de soluciones para una solución determinada mediante el cuadro de diálogo Configuraciones de soluciones en un nuevo tipo de proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b8891d5e68623312049e60730b0239bf7c06e83c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954480"
---
# <a name="project-configuration-for-building"></a>Configuración del proyecto para la compilación
La lista de configuraciones de soluciones de una solución determinada se administra mediante el cuadro de diálogo Configuraciones de soluciones.

 Un usuario puede crear configuraciones de soluciones adicionales, cada una con su propio nombre único. Cuando el usuario crea una nueva configuración de soluciones, el IDE tiene como valor predeterminado el nombre de configuración correspondiente en los proyectos o Debug si no existe ningún nombre correspondiente. Si es necesario, el usuario puede cambiar la selección para cumplir requisitos específicos. La única excepción a este comportamiento es cuando el proyecto admite una configuración que coincida con el nombre de la nueva configuración de soluciones. Por ejemplo, suponga que una solución contiene Project1 y Proyecto2. Project1 tiene configuraciones de proyecto debug, Retail y MyConfig1. Proyecto2 tiene configuraciones de proyecto debug, Retail y MyConfig2.

 Si el usuario crea una nueva configuración de soluciones denominada MyConfig2, Project1 enlaza la configuración de depuración a la configuración de la solución de forma predeterminada. Proyecto2 también enlaza su configuración de MyConfig2 a la configuración de la solución de forma predeterminada.

> [!NOTE]
> El enlace no distingue mayúsculas de minúsculas.

 Cuando el usuario selecciona el elemento de **selección múltiple** en la lista desplegable configuración, el entorno muestra un cuadro de diálogo que proporciona la lista de configuraciones disponibles.

 ![Varias configuraciones](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Varias configuraciones

 Dentro de este cuadro de diálogo, el usuario puede seleccionar una o varias configuraciones. Una vez seleccionados, los valores de propiedad mostrados en el cuadro de diálogo páginas de propiedades reflejan la intersección de los valores de las configuraciones seleccionadas.

 Vea [configuración de soluciones](../../extensibility/internals/solution-configuration.md) para obtener información sobre cómo agregar y cambiar el nombre de configuraciones para soluciones y proyectos.

 Las dependencias del proyecto y el orden de compilación son independientes de la configuración de la solución: es decir, solo se puede configurar un árbol de dependencia para todos los proyectos de la solución. Al hacer clic con el botón derecho en la solución o proyecto y seleccionar la opción **dependencias del proyecto** o **orden de compilación del proyecto** , se abre el cuadro de diálogo **dependencias del proyecto** . También se puede abrir desde el menú **proyecto** .

 ![Dependencias del proyecto](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") Dependencias del proyecto

 Las dependencias del proyecto determinan el orden en el que se compilan los proyectos. Use la pestaña orden de compilación del cuadro de diálogo para ver el orden exacto en que se compilarán los proyectos de una solución y use la pestaña dependencias para modificar el orden de compilación.

> [!NOTE]
> Los proyectos de la lista que tienen las casillas de verificación seleccionadas pero que aparecen atenuados se han agregado en el entorno debido a las dependencias explícitas especificadas por las <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfaces o, y no se pueden cambiar. Por ejemplo, al agregar una referencia de proyecto de un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] proyecto a otro proyecto, se agrega automáticamente una dependencia de compilación que solo se puede quitar eliminando la referencia. Los proyectos cuyas casillas están desactivadas y aparecen atenuadas no se pueden seleccionar porque al hacerlo se crearía un bucle de dependencia (por ejemplo, Project1 dependería de Proyecto2 y Proyecto2 dependería de Project1), lo que paralizaría la compilación.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] los procesos de compilación incluyen las operaciones de compilación y vinculación típicas que se invocan con un solo comando de compilación. También se pueden admitir otros dos procesos de compilación: una operación de limpieza para eliminar todos los elementos de salida de una compilación anterior y una comprobación actualizada para determinar si un elemento de salida de una configuración ha cambiado.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> los objetos devuelven un correspondiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (devuelto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A> ) para administrar sus procesos de compilación. Para notificar el estado de una operación de compilación mientras se está produciendo, las configuraciones realizan llamadas a <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback> , una interfaz implementada por el entorno y cualquier otro objeto interesado en los eventos de estado de la compilación.

 Una vez creado, se pueden usar los valores de configuración para determinar si se pueden ejecutar o no bajo el control del depurador. Las configuraciones implementan <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> para admitir la depuración.

 Después de implementar las dependencias del proyecto, puede manipular mediante programación las dependencias a través del modelo de automatización. Se llama a <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> en el modelo de automatización. No hay ninguna interfaz de nivel de API de VSIP disponible que permita la manipulación directa de las configuraciones del administrador de compilación de soluciones y sus propiedades.

 Además, puede proporcionar una cuadrícula en la ventana dependencias del proyecto. Para obtener más información, consulte [propiedades Mostrar cuadrícula](../../extensibility/internals/properties-display-grid.md).

## <a name="see-also"></a>Vea también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para administrar la implementación](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md)
