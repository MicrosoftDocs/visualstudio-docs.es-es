---
title: Problemas conocidos de contenedores
description: Obtenga más información sobre los problemas conocidos que pueden producirse al instalar Visual Studio Build Tools 2017 en un contenedor de Windows.
ms.custom: ''
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c94c6756e1272b08136f624e9cde63523d630b35
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2018
ms.locfileid: "43139150"
---
# <a name="known-issues-for-containers"></a>Problemas conocidos de contenedores

Hay algunos problemas al instalar Visual Studio en un contenedor Docker.

## <a name="windows-container"></a>Contenedor de Windows

Los problemas conocidos aquí descritos se producen cuando se instala Visual Studio Build Tools 2017 en un contenedor de Windows.

* No se puede instalar Visual Studio en un contenedor basado en la imagen microsoft/windowsservercore:10.0.14393.1593. Las imágenes etiquetadas con versiones anteriores o más recientes de Windows deberían funcionar.
* No se pueden instalar versiones del SDK de Windows anteriores a 10.0.14393. Algunos paquetes no se pueden instalar y las cargas de trabajo que dependen de esos paquetes no funcionarán.
* Pase `-m 2GB` (o más) al compilar la imagen. Algunas cargas de trabajo requieren más memoria de la predeterminada (1 GB) cuando se instalan.
* Configure Docker para usar discos mayores que el valor predeterminado de 20 GB.
* Pase `--norestart` en la línea de comandos. Al redactar este artículo, el intento de reinicio de un contenedor de Windows desde el contenedor devuelve `ERROR_TOO_MANY_OPEN_FILES` al host.
* Si basa la imagen directamente en microsoft/windowsservercore, puede que .NET Framework no se instale correctamente y no se indique ningún error de instalación. El código administrado podría no ejecutarse una vez completada la instalación. En su lugar, base la imagen en [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) o en otra versión más reciente. Por ejemplo, puede ver un error como el siguiente al compilar con MSBuild:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): Error MSB6003: No se pudo ejecutar la tarea ejecutable "csc.exe" especificada. No se pudo cargar el archivo o ensamblado «System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a» o una de sus dependencias. El sistema no puede encontrar el archivo especificado.

## <a name="build-tools-container"></a>Contenedor de Build Tools

Es posible que se produzcan los siguientes problemas conocidos al usar un contenedor de Build Tools. Para ver si se han corregido problemas o si hay otros problemas conocidos, visite https://developercommunity.visualstudio.com.

* Es posible que IntelliTrace no funcione en [algunos escenarios](https://github.com/Microsoft/vstest/issues/940) dentro de un contenedor.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalar Build Tools en un contenedor](build-tools-container.md)
* [Ejemplo avanzado de contenedores](advanced-build-tools-container.md)
* [Identificadores de componentes y cargas de trabajo de Visual Studio Build Tools 2017](workload-component-id-vs-build-tools.md)
