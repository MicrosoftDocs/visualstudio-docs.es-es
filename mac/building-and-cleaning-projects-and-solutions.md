---
title: Compilar y limpiar proyectos y soluciones
description: En este artículo se explica cómo compilar un proyecto en Visual Studio para Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.openlocfilehash: 924bdb08154ecb3caad04cabf7e860bed9204e98
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128457"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Compilar y limpiar proyectos y soluciones

Siga los pasos de este artículo para aprender a compilar, recompilar y limpiar una parte o la totalidad de los proyectos de una solución.

> [!NOTE]
> Este tema se aplica a Visual Studio para Mac. En el caso de Visual Studio en Windows, vea [Compilar y limpiar proyectos y soluciones en Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio).

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Para compilar, recompilar o limpiar toda la solución

1. Seleccione el nodo de la solución en el **Panel de solución**:

    ![Seleccionar el nodo de solución](media/compiling-and-building-image1.png)

2. Seleccione el menú **Compilar** en la barra de menús y, luego, elija una de las siguientes opciones:

    ![seleccionar el elemento de menú compilar todo](media/compiling-and-building-image2.png)

    * Seleccione **Compilar todo** para compilar los archivos y los componentes del proyecto que han cambiado desde la compilación más reciente.

    * Seleccione **Recompilar todo** para "limpiar" la solución y, después, compilar todos los archivos de proyecto y los componentes.

    * Seleccione **Limpiar todo** para eliminar los archivos intermedios y de salida. Cuando solo quedan los archivos de proyecto y componente, se pueden compilar nuevas instancias de archivos intermedios y de salida.

## <a name="to-build-or-rebuild-a-single-project"></a>Para compilar o recompilar un solo proyecto

1. En el **Panel de solución**, seleccione el proyecto.

2. Seleccione el menú **Compilar** en la barra de menús.

3. Seleccione Compilar[NombreDelProyecto], Recompilar[NombreDelProyecto] o Limpiar[NombreDelProyecto].

## <a name="to-stop-a-build"></a>Para detener una compilación

Para detener una compilación, use una de las siguientes opciones:

* Haga clic en el cuadrado rojo del área de estado:

    ![Haga clic en el cuadrado rojo para detener la compilación](media/compiling-and-building-image3.png)

* Use el elemento **Detener** del menú **Compilar**.

* Presione **Cmd+Mayús+Entrar**.

## <a name="see-also"></a>Vea también

- [Compilar y limpiar proyectos y soluciones (Visual Studio en Windows)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)