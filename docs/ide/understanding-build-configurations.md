---
title: Descripción de las configuraciones de compilación
ms.date: 11/04/2016
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
ms.openlocfilehash: eed19993f5339a2f33521ad1233522a29eb0442b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68918703"
---
# <a name="understand-build-configurations"></a>Descripción de las configuraciones de compilación

Se pueden almacenar diferentes configuraciones de propiedades de solución y de proyecto para utilizar en distintos tipos de compilaciones. Para crear, seleccionar, modificar o eliminar una configuración, se puede usar el **Administrador de configuración**. Para abrirlo, en la barra de menús, seleccione **Compilación** >  **, Administrador de configuración**, o simplemente escriba **Configuración** en el cuadro de búsqueda. También se puede usar la lista **Configuraciones de soluciones** de la barra de herramientas **Estándar** para seleccionar una configuración o abrir el **Administrador de configuración**.

> [!NOTE]
> Este tema se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Descripción de las configuraciones de compilación en Visual Studio para Mac](/visualstudio/mac/configurations).

> [!NOTE]
> Si no se pueden encontrar los valores de configuración de soluciones en la barra de herramientas y no se puede tener acceso al **Administrador de configuración**, se puede aplicar la configuración de desarrollo de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Para obtener más información, vea [Cómo: Administración de configuraciones a las que se han aplicado opciones del desarrollador de Visual Basic](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

De forma predeterminada, las configuraciones Debug y Release se incluyen en los proyectos creados mediante plantillas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Una configuración Debug admite la depuración de una aplicación y una configuración Release compila una versión de la aplicación que se puede implementar. Para obtener más información, vea [Cómo: Establecer configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md). También se pueden crear configuraciones de soluciones personalizadas y configuraciones de proyecto. Para obtener más información, vea [Cómo: crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Configuraciones de solución

Una configuración de soluciones especifica el modo en que se van a compilar e implementar los proyectos de la solución. Para modificar una configuración de soluciones o definir una nueva, en el **Administrador de configuración**, en **Configuración de soluciones activas**, seleccione **Editar** o **Nueva**.

Cada entrada del cuadro **Contextos del proyecto** de una configuración de soluciones representa un proyecto de la solución. Para cada combinación de **Configuración de soluciones activas** y de **Plataforma de soluciones activas**, se puede establecer cómo se usa cada proyecto. (Para más información sobre las plataformas de soluciones, vea [Descripción de las plataformas de compilación](../ide/understanding-build-platforms.md)).

> [!NOTE]
> Cuando se define una nueva configuración de solución y se activa la casilla **Crear nuevas configuraciones de proyecto**, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] asigna automáticamente la nueva configuración a todos los proyectos. Del mismo modo, cuando se define una nueva plataforma de solución y se activa la casilla **Crear nuevas plataformas de proyecto**, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] asigna automáticamente la nueva plataforma a todos los proyectos. Además, si se agrega un proyecto destinado a una nueva plataforma, Visual Studio agrega esa plataforma a la lista de plataformas de la solución y la asigna a todos los proyectos.
>
> Todavía se puede modificar los valores de cada proyecto.

La configuración de soluciones activas también proporciona contexto al IDE. Por ejemplo, si se está trabajando en un proyecto y la configuración especifica que se va a compilar para un dispositivo móvil, en el **Cuadro de herramientas** solo se muestran los elementos que se pueden usar en un proyecto de dispositivo móvil.

## <a name="project-configurations"></a>Configuraciones de proyectos
La configuración y la plataforma de destino de proyecto se utilizan conjuntamente para especificar las propiedades que se desean utilizar al compilar el proyecto. Un proyecto puede tener un conjunto diferente de definiciones de propiedad para cada combinación de configuración y plataforma. Para modificar las propiedades de un proyecto, se pueden utilizar sus Páginas de propiedades. (En el **Explorador de soluciones**, abra el menú contextual del proyecto y seleccione **Propiedades**).

Para cada configuración de proyecto se pueden definir las propiedades dependientes de la configuración que se necesiten. Por ejemplo, para una compilación determinada, se puede establecer qué elementos del proyecto se van a incluir, qué archivos de salida se van a crear, dónde se van a colocar y cómo se van a optimizar.

Las configuraciones de proyecto pueden diferir considerablemente. Por ejemplo, las propiedades de una conexión pueden especificar que el archivo de salida está optimizado para ocupar el espacio mínimo, mientras que otra configuración puede especificar que el archivo ejecutable se ejecuta a la velocidad máxima.

Las configuraciones de proyecto se almacenan por solución, no por usuario, para que pueda compartirlas un equipo.

Aunque las dependencias de proyecto sean independientes de la configuración, solo se compilan los proyectos especificados en la configuración de soluciones activas.

## <a name="how-visual-studio-assigns-project-configurations"></a>Cómo asigna Visual Studio las configuraciones de proyecto
Si se define una nueva configuración de soluciones y no se copian valores de una configuración existente, Visual Studio utiliza los siguientes criterios para asignar las configuraciones de proyecto predeterminadas. Los criterios se evalúan en el orden mostrado.

1. Si un proyecto tiene un nombre de configuración ( *\<nombre de configuración> \<nombre de plataforma>* ) que coincide exactamente con el nombre de la nueva configuración de soluciones, se asignará dicha configuración. En los nombres de configuraciones no se distingue entre mayúsculas y minúsculas.

2. Si el proyecto tiene un nombre de configuración en el que la parte del nombre de configuración coincide con la nueva configuración de soluciones, se asigna esa configuración, independientemente de que la parte de plataforma coincida o no.

3. Si no hay ninguna coincidencia, se asigna la primera configuración que aparece en el proyecto.

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
- [Modificadores de línea de comandos para Devenv](../ide/reference/devenv-command-line-switches.md)
- [Descripción de las configuraciones de compilación (Visual Studio para Mac)](/visualstudio/mac/configurations)