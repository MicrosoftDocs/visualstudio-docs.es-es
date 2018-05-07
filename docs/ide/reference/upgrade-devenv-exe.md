---
title: -Upgrade (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e4366235973a3e4aa090f5a2c65b346d40067c7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
Actualiza el archivo de solución y todos sus archivos de proyecto, o el archivo de proyecto especificado, a los formatos actuales de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para estos archivos.

## <a name="syntax"></a>Sintaxis

```
devenv SolutionFile | ProjectFile /upgrade
```

## <a name="arguments"></a>Argumentos
 `SolutionFile`

 Necesario si va a actualizar una solución completa y sus proyectos. Ruta de acceso y nombre de un archivo de solución. Se puede escribir solo el nombre del archivo de solución o una ruta de acceso completa y el nombre del archivo de solución. Si la carpeta o el archivo especificados no existen todavía, se crean.

 `ProjectFile`

 Necesario si va a actualizar un único proyecto. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Se puede escribir solo el nombre del archivo de proyecto o una ruta de acceso completa y el nombre del archivo de proyecto. Si la carpeta o el archivo especificados no existen todavía, se crean.

## <a name="remarks"></a>Comentarios
 Se crean automáticamente copias de seguridad y se copian en un directorio denominado Backup que se crea en el directorio actual.

 Se deben desproteger las soluciones o los proyectos bajo el control de código fuente antes de poderse actualizar.

 Al utilizar el modificador `/upgrade` no se inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Los resultados de la actualización se pueden ver en el informe de actualización para el lenguaje de desarrollo de la solución o el proyecto. No se devuelve ninguna información de error o de uso. Para obtener más información sobre cómo actualizar proyectos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], vea [Portar, migrar y actualizar proyectos de Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a>Ejemplo
 En este ejemplo se actualiza un archivo de solución denominado "MyProject.sln" en la carpeta predeterminada para las soluciones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

```
devenv "MyProject.sln" /upgrade
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)