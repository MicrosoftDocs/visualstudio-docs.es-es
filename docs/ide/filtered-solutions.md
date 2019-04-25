---
title: Carga de un subconjunto de proyectos
ms.date: 12/04/2018
ms.prod: visual-studio-dev16
ms.topic: conceptual
helpviewer_keywords:
- filtered solution
- solution filtering
author: gewarren
ms.author: stsu
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 67ebbd94298c3325560b64945bed51c09db93833
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "57983889"
---
# <a name="filtered-solutions-in-visual-studio"></a>Soluciones filtradas en Visual Studio

**Novedades de Visual Studio 2019**

Los equipos grandes de desarrollo suelen colaborar mediante una sola solución de gran tamaño con muchos proyectos. Sin embargo, los desarrolladores individuales normalmente trabajan en un pequeño subconjunto de estos proyectos. Para mejorar el rendimiento al abrir soluciones de gran tamaño, Visual Studio 2019 presenta el *filtrado de soluciones*. El filtrado de soluciones permite abrir una solución únicamente con proyectos selectivos cargados. El hecho de cargar un subconjunto de proyectos en una solución reduce el tiempo de carga, compilación y pruebas de la solución, y permite una revisión más específica.

A continuación se enumeran las características disponibles:

- Puede obtener en código con mayor rapidez abriendo una solución sin tener que cargar ninguno de sus proyectos. Una vez abierta la solución, podrá elegir los proyectos que quiera cargar.

- Cuando vuelva a abrir una solución, Visual Studio recordará los proyectos que haya cargado en la sesión anterior y solo cargará dichos proyectos.

- Puede crear un archivo de filtro de soluciones para guardar una o varias configuraciones de carga de proyectos, o bien compartirlas con sus compañeros.

## <a name="open-a-filtered-solution"></a>Apertura de una solución filtrada

Para abrir una solución con solo algunos de los proyectos cargados, siga estos pasos:

1. Elija **Archivo** > **Abrir** > **Proyecto o solución** en la barra de menús.

2. En el cuadro de diálogo **Abrir proyecto**, seleccione la solución y, a continuación, seleccione **No cargar los proyectos**.

   ![Cuadro de diálogo Abrir proyecto de Visual Studio con la opción para no cargar proyectos seleccionada](media/filtered-solutions/do-not-load-projects.png)

3. Pulse **Abrir**.

   La solución se abre con todos sus proyectos descargados.

4. En el **Explorador de soluciones**, seleccione los proyectos que quiera cargar (presione **Ctrl** y haga clic para seleccionar más de un proyecto) y, luego, haga doble clic con el botón derecho en el proyecto y elija **Volver a cargar el proyecto**.

   ![Volver a cargar varios proyectos en el Explorador de soluciones de Visual Studio](media/filtered-solutions/reload-project.png)

   Visual Studio recordará los proyectos que se carguen la próxima vez que abra la solución localmente.

## <a name="toggle-unloaded-project-visibility"></a>Alternancia de la visibilidad del proyecto descargado

Puede optar por ver todos los proyectos en la solución o solo los que están cargados mediante una de las siguientes opciones en el **Explorador de soluciones**:

- Haga clic en la solución y seleccione **Mostrar proyectos descargados** u **Ocultar proyectos descargados**.

- Seleccione el botón **Mostrar todos los archivos** para alternar la visibilidad de los proyectos descargados.

   ![Botón Mostrar todos los archivos en el Explorador de soluciones de Visual Studio](media/filtered-solutions/show-all-files.PNG)

## <a name="solution-filter-files"></a>Archivos de filtro de soluciones

Para compartir la configuración de carga de proyecto o confirmarla en el control de código fuente, puede crear un archivo de filtro de soluciones (extensión *.slnf*). Al abrir un archivo de filtro de soluciones, la solución se abrirá en Visual Studio con los proyectos especificados cargados y todos los proyectos descargados ocultos. También puede [alternar](#toggle-unloaded-project-visibility) para ver los proyectos descargados.

Los archivos de filtro de soluciones se diferencian visualmente de los archivos de soluciones habituales por el glifo de embudo adicional en el icono situado junto a la solución en el **Explorador de soluciones**. El nombre del filtro y el número de proyectos cargados también se muestran al lado del nombre de la solución.

![Archivo de filtro de soluciones abierto en el Explorador de soluciones de Visual Studio](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> Si se agregan proyectos nuevos a la solución original después de crear el archivo de filtro de soluciones, aparecerán como proyectos descargados en el **Explorador de soluciones**.

### <a name="create-a-solution-filter-file"></a>Creación de un archivo de filtro de soluciones

1. En el **Explorador de soluciones**, haga clic con el botón derecho en la solución y seleccione **Guardar como filtro de soluciones**.

   ![Menú Guardar como filtro de soluciones en el Explorador de soluciones de Visual Studio](media/filtered-solutions/save-as-solution-filter.png)

2. Elija un nombre y una ubicación para el archivo de filtro de soluciones.

Después de crear un archivo de filtro de soluciones, se agregará a la lista **Proyectos y soluciones recientes** para facilitar el acceso:

![Apertura de elementos en Visual Studio](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>Vea también

- [Personalización del anidamiento de archivos en el Explorador de soluciones](file-nesting-solution-explorer.md)
- [Optimización del rendimiento de Visual Studio](optimize-visual-studio-performance.md)
