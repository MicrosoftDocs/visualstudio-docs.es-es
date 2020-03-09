---
title: Descripción de las configuraciones de compilación
ms.date: 01/20/2020
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a37d4fa5dc92253b94dc64590c9df5fec7703ceb
ms.sourcegitcommit: b016ea260856264eee730ee8cbcab198314a7ece
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2020
ms.locfileid: "77904170"
---
# <a name="understand-build-configurations"></a>Descripción de las configuraciones de compilación

Necesita configuraciones de compilación para compilar los proyectos con otros valores. Por ejemplo, **Debug** y **Release** son configuraciones, y se usan distintas opciones de compilador en consonancia al compilarlas.  Una configuración está activa y se indica en la barra de comandos en la parte superior del IDE.

![Configuración activa](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Descripción de las configuraciones de compilación en Visual Studio para Mac](/visualstudio/mac/configurations).

La configuración y el control de plataforma donde se almacenan los archivos de salida compilados. Normalmente, cuando Visual Studio compila el proyecto, la salida se coloca en una subcarpeta del proyecto designada con la configuración activa (por ejemplo, *bin/Debug/x86*), pero se puede cambiar.

Puede crear sus propias configuraciones de compilación en el nivel de solución y proyecto. La configuración de soluciones determina qué proyectos se incluyen en la compilación cuando esa configuración está activa. Solo se compilarán los proyectos que se especifiquen en la configuración de soluciones activa. Si se seleccionan varias plataformas de destino en el Administrador de configuración, se compilan todos los proyectos que se aplican a esa plataforma. La configuración del proyecto determina qué opciones del compilador y valores de compilación se usan al compilar el proyecto.

Para crear, seleccionar, modificar o eliminar una configuración, se puede usar el **Administrador de configuración**. Para abrirlo, en la barra de menús, seleccione **Compilación** >  **, Administrador de configuración**, o simplemente escriba **Configuración** en el cuadro de búsqueda. También se puede usar la lista **Configuraciones de soluciones** de la barra de herramientas **Estándar** para seleccionar una configuración o abrir el **Administrador de configuración**.

![Administrador de configuración](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> Si no se pueden encontrar los valores de configuración de soluciones en la barra de herramientas y no se puede tener acceso al **Administrador de configuración**, se puede aplicar la configuración de desarrollo de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Para obtener más información, vea [Cómo: Administración de configuraciones a las que se han aplicado opciones del desarrollador de Visual Basic](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

De forma predeterminada, las configuraciones **Debug** y **Release** se incluyen en los proyectos creados mediante plantillas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Una configuración **Debug** admite la depuración de una aplicación y una configuración **Release** compila una versión de la aplicación que se puede implementar. Para obtener más información, vea [Cómo: Establecer configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md). También se pueden crear configuraciones de soluciones personalizadas y configuraciones de proyecto. Para obtener más información, vea [Cómo: crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Configuraciones de solución

Una configuración de soluciones especifica el modo en que se van a compilar e implementar los proyectos de la solución. Para modificar una configuración de soluciones o definir una nueva, en el **Administrador de configuración**, en **Configuración de soluciones activas**, seleccione **Editar** o **Nueva**.

Cada entrada del cuadro **Contextos del proyecto** de una configuración de soluciones representa un proyecto de la solución. Para cada combinación de **Configuración de soluciones activas** y de **Plataforma de soluciones activas**, se puede establecer cómo se usa cada proyecto. (Para más información sobre las plataformas de soluciones, vea [Descripción de las plataformas de compilación](../ide/understanding-build-platforms.md)).

Cuando se define una nueva configuración de solución y se activa la casilla **Crear nuevas configuraciones de proyecto**, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] asigna automáticamente la nueva configuración a todos los proyectos. Del mismo modo, cuando se define una nueva plataforma de solución y se activa la casilla **Crear nuevas plataformas de proyecto**, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] asigna automáticamente la nueva plataforma a todos los proyectos. Además, si se agrega un proyecto destinado a una nueva plataforma, Visual Studio agrega esa plataforma a la lista de plataformas de la solución y la asigna a todos los proyectos. Todavía se puede modificar los valores de cada proyecto.

La configuración de soluciones activas también proporciona contexto al IDE. Por ejemplo, si se está trabajando en un proyecto y la configuración especifica que se va a compilar para un dispositivo móvil, en el **Cuadro de herramientas** solo se muestran los elementos que se pueden usar en un proyecto de dispositivo móvil.

## <a name="project-configurations"></a>Configuraciones de proyectos

La configuración y la plataforma a la que se dirige un proyecto se usan conjuntamente para especificar los valores de compilación y las opciones del compilador que se utilizarán al compilar el proyecto. Un proyecto puede tener unos valores diferentes para cada combinación de configuración y plataforma. Para modificar las propiedades de un proyecto, abra el menú contextual del proyecto en el **Explorador de soluciones** y, luego, elija **Propiedades**.  En la parte superior de la pestaña **Compilación** del diseñador de proyectos, elija una configuración activa para editar sus valores de compilación.

![Configuraciones del diseñador de proyectos](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="building-multiple-configurations"></a>Compilación de varias configuraciones

Al compilar una solución con el comando **Compilar** > **Compilar solución**, Visual Studio solo compila la configuración activa. Se compilan todos los proyectos que se especifican en la configuración de la solución y la única configuración de proyecto compilada es la que se especifica en la configuración de la solución activa y en la plataforma de la solución activa, que se muestra en la barra de herramientas de Visual Studio. Por ejemplo, **Depurar** y **x86**. No se compilan otras configuraciones y plataformas definidas.

Si desea compilar varias configuraciones y plataformas en una acción, puede usar la opción **Compilar** > **Compilación por lotes** en Visual Studio. Para obtener acceso a esta característica, presione **Ctrl**+**Q** para abrir el cuadro de búsqueda y escriba `Batch build`. La compilación por lotes no está disponible para todos los tipos de proyectos. Vea [Cómo: Compilación de varias configuraciones simultáneamente](how-to-build-multiple-configurations-simultaneously.md).

## <a name="how-visual-studio-assigns-project-configurations"></a>Cómo asigna Visual Studio las configuraciones de proyecto

Si se define una nueva configuración de soluciones y no se copian valores de una configuración existente, Visual Studio utiliza los siguientes criterios para asignar las configuraciones de proyecto predeterminadas. Los criterios se evalúan en el orden mostrado.

1. Si un proyecto tiene un nombre de configuración ( *\<nombre de configuración> \<nombre de plataforma>* ) que coincide exactamente con el nombre de la nueva configuración de soluciones, se asignará dicha configuración. En los nombres de configuraciones no se distingue entre mayúsculas y minúsculas.

1. Si el proyecto tiene un nombre de configuración en el que la parte del nombre de configuración coincide con la nueva configuración de soluciones, se asigna esa configuración, independientemente de que la parte de plataforma coincida o no.

1. Si no hay ninguna coincidencia, se asigna la primera configuración que aparece en el proyecto.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Cómo asigna Visual Studio las configuraciones de soluciones

Cuando se crea una configuración de proyecto (en el **Administrador de configuración**, al seleccionar **Nuevo** en el menú desplegable de la columna **Configuración** para ese proyecto) y se activa la casilla **Crear nuevas configuraciones de solución**, Visual Studio busca una configuración de soluciones con el mismo nombre para compilar el proyecto en cada una de las plataformas que se admiten. En algunos casos, Visual Studio cambia el nombre de las configuraciones de soluciones existentes o define otras nuevas.

Visual Studio utiliza los siguientes criterios para asignar configuraciones de soluciones.

- Si una configuración de proyectos no especifica ninguna plataforma o especifica solo una, se busca o se agrega una configuración de soluciones cuyo nombre coincida con el de la nueva configuración de proyecto. El nombre predeterminado de esta configuración de soluciones no incluye el nombre de plataforma, sino que adopta el formato *\<nombre de la configuración del proyecto>* .

- Si un proyecto admite varias plataformas, se busca o se agrega una configuración de soluciones para cada plataforma admitida. El nombre de cada configuración de soluciones incluye tanto el nombre de configuración del proyecto como el nombre de la plataforma y tiene el formato *\<nombre de la configuración del proyecto> \<nombre de plataforma>* .

## <a name="see-also"></a>Vea también

- [Tutorial: Creación de una aplicación](../ide/walkthrough-building-an-application.md)
- [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md)
- [Soluciones y proyectos](../ide/solutions-and-projects-in-visual-studio.md)
- [Referencia de compilación de C/C++](/cpp/build/reference/c-cpp-building-reference)
- [Descripción de las plataformas de compilación](understanding-build-platforms.md)
- [Descripción de las configuraciones de compilación (Visual Studio para Mac)](/visualstudio/mac/configurations)
