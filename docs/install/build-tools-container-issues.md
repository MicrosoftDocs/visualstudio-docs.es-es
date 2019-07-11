---
title: Problemas conocidos de contenedores
description: Obtenga más información sobre los problemas conocidos que pueden producirse al instalar Visual Studio Build Tools en un contenedor de Windows.
ms.date: 04/18/2018
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9953a1c58ea6ddd13ca0555959ed621905ba710a
ms.sourcegitcommit: c7b9ab1bc19d74b635c19b1937e92c590dafd736
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552883"
---
# <a name="known-issues-for-containers"></a>Problemas conocidos de contenedores

Hay algunos problemas al instalar Visual Studio en un contenedor Docker.

## <a name="windows-container"></a>Contenedor de Windows

Los problemas conocidos aquí descritos se producen cuando se instala Visual Studio Build Tools en un contenedor de Windows.

::: moniker range="vs-2017"

* No se puede instalar Visual Studio en un contenedor basado en la imagen microsoft/windowsservercore:10.0.14393.1593. Las imágenes etiquetadas con versiones de Windows anteriores o posteriores a 10.0.14393 deberían funcionar.

* No se puede instalar la versión 10.0.14393 del SDK de Windows ni versiones anteriores a esta. Algunos paquetes no se pueden instalar y las cargas de trabajo que dependen de esos paquetes no funcionarán.

::: moniker-end

* Pase `-m 2GB` (o más) al compilar la imagen. Algunas cargas de trabajo requieren más memoria de la predeterminada (1 GB) cuando se instalan.
* Configure Docker para usar discos mayores que el valor predeterminado de 20 GB.
* Pase `--norestart` en la línea de comandos. Al redactar este artículo, el intento de reinicio de un contenedor de Windows desde el contenedor devuelve `ERROR_TOO_MANY_OPEN_FILES` al host.
* Si basa la imagen directamente en microsoft/windowsservercore, puede que .NET Framework no se instale correctamente y no se indique ningún error de instalación. Es posible que el código administrado no se ejecute una vez completada la instalación. En su lugar, base la imagen en [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) o en otra versión posterior. Por ejemplo, es posible al compilar con MSBuild que vea un error similar al siguiente:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): error MSB6003: No se pudo ejecutar la tarea ejecutable especificada "csc.exe". No se pudo cargar el archivo o ensamblado «System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a» o una de sus dependencias. El sistema no puede encontrar el archivo especificado.

::: moniker range="vs-2017"

* Visual Studio 2017 versión 15.8 o cualquier versión anterior (de cualquier producto) no se pueden instalar en mcr.microsoft.com/windows/servercore:1809 o posterior. Vea https://aka.ms/setup/containers/servercore1809 para obtener más información.

::: moniker-end

## <a name="build-tools-container"></a>Contenedor de Build Tools

Es posible que se produzcan los siguientes problemas conocidos al usar un contenedor de Build Tools. Para ver si se han corregido problemas o si hay otros problemas conocidos, visite https://developercommunity.visualstudio.com.

* Es posible que IntelliTrace no funcione en [algunos escenarios](https://github.com/Microsoft/vstest/issues/940) dentro de un contenedor.
* En versiones anteriores de Docker para Windows, el tamaño de la imagen del contenedor predeterminado es de solo 20 GB y no cabrá en Build Tools. Siga las [instrucciones para cambiar el tamaño de la imagen](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/container-storage#image-size) a 127 GB o más.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalar Build Tools en un contenedor](build-tools-container.md)
* [Ejemplo avanzado de contenedores](advanced-build-tools-container.md)
* [Identificadores de componente y carga de trabajo de Visual Studio Build Tools](workload-component-id-vs-build-tools.md)
