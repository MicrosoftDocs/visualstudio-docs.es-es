---
title: -Upgrade (devenv.exe)
description: Obtenga información sobre cómo usar el modificador Upgrade de la línea de comandos de devenv para actualizar el archivo de solución y todos sus archivos de proyecto, o bien el archivo de proyecto especificado, a los formatos actuales de Visual Studio para estos archivos.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2bb0565783efb27cf4194bb25982ee0f717be776
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040958"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)

Actualiza el archivo de solución y todos sus archivos de proyecto (o el archivo de proyecto especificado) a los formatos actuales de Visual Studio para estos archivos.

## <a name="syntax"></a>Sintaxis

```shell
devenv {SolutionFile|ProjectFile} /Upgrade [/Out OutputFilename]
```

## <a name="arguments"></a>Argumentos

- *SolutionFile*

  Necesario si va a actualizar una solución completa y sus proyectos. Ruta de acceso y nombre de un archivo de solución. Se puede escribir solo el nombre del archivo de solución o una ruta de acceso completa y el nombre del archivo de solución. Si la carpeta o el archivo indicado no existen aún, se crearán.

- *ProjectFile*

  Necesario si va a actualizar un único proyecto. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Se puede escribir solo el nombre del archivo de proyecto o una ruta de acceso completa y el nombre del archivo de proyecto. Si la carpeta o el archivo indicado no existen aún, se crearán.

- `/Out` *OutputFilename*

  Opcional. Nombre de un archivo que quiera enviar al resultado de la herramienta. Si el archivo ya existe, la herramienta anexa el resultado al final del archivo.

## <a name="remarks"></a>Comentarios

Se guardan automáticamente copias de seguridad en un directorio denominado Backup que se crea en el directorio actual.

Se deben desproteger las soluciones o los proyectos bajo el control de código fuente antes de poderse actualizar.

Si usa el modificador `/Upgrade`, Visual Studio no se abrirá. Los resultados de la actualización se pueden ver en el informe de actualización para el lenguaje de desarrollo de la solución o el proyecto. No se devuelve ninguna información de error o de uso. Para obtener más información sobre cómo actualizar proyectos en Visual Studio, vea [Portar, migrar y actualizar proyectos de Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a>Ejemplo

En este ejemplo se actualiza un archivo de solución denominado "MyProject.sln".

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
