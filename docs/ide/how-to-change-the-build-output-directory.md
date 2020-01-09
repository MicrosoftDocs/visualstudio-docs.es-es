---
title: Procedimiento Cambiar el directorio de salida de compilación
ms.date: 05/15/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 732e48bf5cbea8534cc5c90ac5af80df0cc93e7b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594388"
---
# <a name="how-to-change-the-build-output-directory"></a>Procedimiento Cambiar el directorio de salida de compilación

Puede especificar la ubicación de salida generada por el proyecto según la configuración (para depuración, versión o ambos).

## <a name="change-the-build-output-directory"></a>Cambiar el directorio de salida de compilación

1. Para abrir las páginas de propiedades del proyecto, haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** y seleccione **Propiedades**.

2. Seleccione la pestaña adecuada según el tipo de proyecto:

   - Para C#, seleccione la pestaña **Compilar**.
   - Para Visual Basic, seleccione la pestaña **Compilar**.
   - Para C++ o JavaScript, seleccione la pestaña **General**.

3. En la lista desplegable de configuración de la parte superior, seleccione la configuración cuya ubicación del archivo de salida quiera cambiar (**Depuración**, **Versión** o **Todas las configuraciones**).

4. Busque la entrada de la ruta de acceso de salida en la página: varía según el tipo de proyecto:

   - **Ruta de acceso de salida** para proyectos de C# y JavaScript
   - **Ruta de acceso de salida de compilación** para proyectos de Visual Basic
   - **Directorio de salida** para proyectos de Visual C++

   Escriba la ruta de acceso donde se va a generar la salida (absoluta o relativa con respecto al directorio raíz del proyecto) o seleccione **Examinar** para ir a esa carpeta.

   ![Propiedad de ruta de acceso de salida de un proyecto de C# de Visual Studio](media/output-path.png)
   
   > [!NOTE]
   > Algunos proyectos incluirán de forma predeterminada el marco y el tiempo de ejecución en la ruta de acceso de compilación. Para cambiar esto, haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones**, seleccione **Editar archivo de proyecto** y agregue lo siguiente:
   > ```xml
   > <PropertyGroup>
   >   <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
   >   <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
   > </PropertyGroup>
   > ```

> [!TIP]
> Si la salida no se genera en la ubicación especificada, asegúrese de que va a crear la configuración correspondiente (por ejemplo, **Depuración** o **Versión**) al seleccionarla en la barra de menús de Visual Studio.
>
> ![Selector de configuración de compilación en Visual Studio 2019](media/build-configuration-chooser.png)

## <a name="see-also"></a>Vea también

- [Página Compilar, Diseñador de proyectos (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Página Propiedad general (Proyecto)](/cpp/build/reference/general-property-page-project)
- [Compilar y generar](../ide/compiling-and-building-in-visual-studio.md)
