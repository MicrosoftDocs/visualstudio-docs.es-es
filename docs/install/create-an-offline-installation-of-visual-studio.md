---
title: Crear una instalación sin conexión de Visual Studio
description: Descubra cómo instalar Visual Studio sin conexión.
ms.custom: ''
ms.date: 01/17/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d19eabe10234ca2a1670ae04f99a45a85a6cac14
ms.sourcegitcommit: 6b092e7d466377f06913d49d183dbbdca16730f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2018
ms.locfileid: "43138882"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Crear una instalación sin conexión de Visual Studio 2017

Hemos diseñado un instalador de Visual Studio 2017 que funciona bien en una amplia variedad de condiciones de red y máquina.

- El nuevo modelo basado en la carga de trabajo implica que deberá descargar mucho menos contenido que con las versiones anteriores de Visual Studio: tan solo 300 MB para la instalación más pequeña.
- En comparación con un archivo ZIP o "ISO" genérico, solo se descargan los paquetes necesarios para su equipo. Por ejemplo, no se descargan los archivos de 64 bits si no los necesita.
- Durante el proceso de instalación, probaremos tres tecnologías de descarga diferentes (WebClient, BITS y WinInet) para minimizar la interferencia con software antivirus y de servidor proxy.
- Los archivos que necesitará para instalar Visual Studio se distribuyen en una red de entrega global, así que podemos obtenerlos de un servidor local.

Se recomienda probar el [instalador web de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), ya que creemos que será una buena experiencia.

 > [!div class="button"]
 > [Descargar Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

Si quiere realizar una instalación sin conexión porque su conexión de Internet no está disponible o no es confiable, vea [Instalación de Visual Studio 2017 en entornos de red de bajo ancho de banda o poco confiables](../install/install-vs-inconsistent-quality-network.md). Puede usar la línea de comandos para crear una caché local de los archivos necesarios para completar una instalación sin conexión. Este proceso reemplaza los archivos ISO disponibles para las versiones anteriores.

> [!NOTE]
> Si es un administrador de empresa que quiere realizar una implementación de Visual Studio 2017 en una red de estaciones de trabajo del cliente con firewall desde Internet, vea las páginas [Creación de una instalación de red de Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) y [Instalar los certificados necesarios para la instalación sin conexión de Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]
