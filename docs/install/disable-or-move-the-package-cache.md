---
title: Deshabilitación o traslado de la caché de paquetes
description: Obtenga información sobre cómo deshabilitar, habilitar o mover la caché de paquetes para las implementaciones de Visual Studio.
ms.date: 04/14/2017
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0584673880a56bbde0ef44ad14c24acca252c5a2
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307484"
---
# <a name="disable-or-move-the-package-cache"></a>Deshabilitación o traslado de la caché de paquetes

La caché de paquetes proporciona un origen de paquetes instalados en caso de que tenga que reparar Visual Studio u otros productos relacionados cuando no disponga de conexión a Internet. Aunque es posible que con algunas unidades de disco o instalaciones de sistemas, no pueda conservar todos esos paquetes.
El instalador los descargará cuando sea necesario; así que si quiere guardar o recuperar espacio en disco, puede deshabilitar o mover la caché de paquetes.

## <a name="disable-the-package-cache"></a>Deshabilitación de la caché de paquetes

Antes de instalar, modificar o reparar Visual Studio u otros productos con el nuevo instalador, puede iniciar el instalador pasándole el modificador `--nocache`.

```shell
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Cualquier operación que realice en cualquier producto quitará los paquetes existentes para ese producto y evitará que se guarde ningún paquete después de que se ha instalado. Si modifica o repara Visual Studio y se necesitan paquetes, se descargarán automáticamente y se quitarán una vez instalados.

Si desea volver a habilitar la caché, pase en su lugar `--cache`. Solo se almacenan en caché los paquetes necesarios, así que si tiene que restaurar todos los paquetes, debe reparar Visual Studio antes de desconectarse de la red.

```shell
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

También puede configurar la  [directiva del Registro](set-defaults-for-enterprise-deployments.md)`KeepDownloadedPayloads` para deshabilitar la caché antes de instalar, modificar o reparar Visual Studio.

## <a name="move-the-package-cache"></a>Traslado de la caché de paquetes

Una configuración común del sistema es tener instalado Windows en una SSD con uno o varios discos duros más grandes pensando en las necesidades de desarrollo, como el código fuente, los archivos binarios del programa, etc. Si desea trabajar sin conexión, puede mover en su lugar la caché de paquetes.

Actualmente, esto solo se puede hacer si se configura la  [directiva del Registro](set-defaults-for-enterprise-deployments.md)`CachePath` antes de instalar, modificar o reparar Visual Studio.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalación de Visual Studio](install-visual-studio.md)
* [Establecimiento de valores predeterminados para implementaciones empresariales](set-defaults-for-enterprise-deployments.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
