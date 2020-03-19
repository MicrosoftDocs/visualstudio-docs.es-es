---
title: -UseEnv (devenv.exe)
ms.date: 01/10/2019
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35808b27964b3ca8fa0488f1be2ce6dc5530b3dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596401"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Inicia Visual Studio y carga variables de entorno específicas para la compilación.

> [!NOTE]
> Este modificador se instala con la carga de trabajo **Desarrollo para el escritorio con C++** .

## <a name="syntax"></a>Sintaxis

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argumentos

- *SolutionName*

  Ruta de acceso completa y nombre de un archivo de solución.

- *ProjectName*

  Ruta de acceso completa y nombre de un archivo de proyecto.

## <a name="remarks"></a>Comentarios

Este modificador afecta al IDE de Visual Studio en las propiedades del proyecto para **Directorios de VC++** . Si especifica el modificador `/UseEnv`, en el nodo **Directorios de VC++** , se mostrarán los valores de las variables de entorno PATH, INCLUDE, LIBPATH y LIB. (También se muestran valores para **Directorios de archivos de código fuente** y **Excluir directorios**). De lo contrario, el nodo reemplaza las variables de entorno por cinco valores de directorio: **Directorios de archivos ejecutables**, **Directorios de archivos de inclusión**, **Directorios de referencia**, **Directorios de bibliotecas** y **Directorios de biblioteca WinRT**.

> [!TIP]
> Para acceder a las propiedades del proyecto, haga clic con el botón derecho en un proyecto de C++ y seleccione **Propiedades**. En el cuadro de diálogo **Páginas de propiedades**, seleccione **Propiedades de configuración** y, después, **Directorios de VC++** .

Al especificar un nombre de proyecto con este modificador, en la herramienta se muestran las variables de entorno de todos los proyectos en la solución primaria del proyecto.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra Visual Studio y se cargan las variables de entorno en las páginas de propiedades de la solución de `MySolution`.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [Página de propiedades de directorios de VC++ (Windows)](/cpp/build/reference/vcpp-directories-property-page)
