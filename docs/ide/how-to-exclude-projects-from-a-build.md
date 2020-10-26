---
title: Procedimiento Exclusión de proyectos de una compilación
description: Aprenda a usar Visual Studio para compilar una solución sin compilar todos los proyectos que contiene.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b0e164c24770048495d16da852523b3dd50a43a
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136906"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Procedimiento Exclusión de proyectos de una compilación

Para compilar una solución no es necesario compilar todos los proyectos que contiene. Por ejemplo, se puede excluir un proyecto que interrumpa la compilación y, a continuación, compilar el proyecto tras haber investigado y resuelto los problemas.

Un proyecto se puede excluir de las siguientes maneras:

- Eliminándolo temporalmente de la configuración de soluciones activa.

- Creando una configuración de soluciones que no incluya el proyecto.

Para obtener más información, vea [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md).

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Para eliminar temporalmente un proyecto de la configuración de soluciones activa

1. En la barra de menús, elija **Compilar** > **Administrador de configuración** .

2. En la tabla **Contextos del proyecto** , busque el proyecto que quiere excluir de la compilación.

3. En la columna **Compilar** del proyecto, desactive la casilla.

4. Pulse el botón **Cerrar** y, después, vuelva a compilar la solución.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Para crear una configuración de soluciones que excluya un proyecto

1. En la barra de menús, elija **Compilar** > **Administrador de configuración** .

2. En la lista **Configuración de soluciones activas** , elija **\<New>** .

3. En el cuadro **Nombre** , escriba un nombre para la configuración de soluciones.

4. En la lista **Copiar configuración de** , pulse la configuración de soluciones en la que quiera basar la nueva configuración (por ejemplo, **Depurar** ) y, después, pulse el botón **Aceptar** .

5. En el cuadro de diálogo **Administrador de configuración** , desactive la casilla de la columna **Compilar** del proyecto que quiera excluir y, después, pulse el botón **Cerrar** .

6. En la barra de herramientas **Estándar** , compruebe que la nueva configuración de soluciones sea la configuración activa en el cuadro **Configuraciones de soluciones** .

7. En la barra de menús, elija **Compilación** > **Recompilar solución** .

## <a name="skipped-projects"></a>Proyectos omitidos

Los proyectos se pueden omitir durante la compilación porque no están actualizados o porque están excluidos de la configuración. Visual Studio usa MSBuild para compilar los proyectos. MSBuild solo compila un destino si la salida es más antigua que la entrada, en función de lo que determinen las marcas de tiempo del archivo. Para forzar una recompilación, use el comando **Compilar** > **Recompilar solución** .

En el panel **Compilar** de la ventana **Salida** de Visual Studio se informa del número de proyectos actualizados, así como el número de proyectos compilados correctamente, con errores y omitidos. El recuento de proyectos omitidos no incluye los que no se compilaron porque estaban actualizados. Si los proyectos se excluyen de la configuración activa, se omitirán durante la compilación. En la salida de la compilación, verá un mensaje en el que se indica que el proyecto se ha omitido:

```output
2>------ Skipped Build: Project: ConsoleApp2, Configuration: Debug x86 ------
2>Project not selected to build for this solution configuration
```

Para averiguar por qué se ha omitido un proyecto, tenga en cuenta la configuración activa (`Debug x86` en el ejemplo anterior) y elija **Compilar** > **Configuration Manager** . Puede ver o cambiar los proyectos que se omiten de cada configuración, tal como se describe en este artículo.

## <a name="see-also"></a>Vea también

- [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md)
- [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md)
- [Cómo: Compilación de varias configuraciones simultáneamente](../ide/how-to-build-multiple-configurations-simultaneously.md)
