---
title: Guía de Visual Studio Enterprise
description: Configure y solucione problemas de Visual Studio en un entorno empresarial.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e5e8a28ac89c2bea85aee8323060bf948266ad2e
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547393"
---
# <a name="visual-studio-enterprise-guide"></a>Guía de Visual Studio Enterprise
Si desea ahorrar tiempo mientras su empresa se ejecuta en Visual Studio, comience aquí. En esta guía empresarial se incluyen sugerencias que pueden ayudarle a instalar y actualizar Visual Studio en escenarios empresariales comunes, desbloquearle si tiene problemas y obtener información sobre cómo informar de un problema si necesita más ayuda. 

## <a name="get-started"></a>Primeros pasos 
Obtenga información sobre cómo implementar Visual Studio en su empresa en entornos conectados en red y sin conexión.

- **[Habilitación de actualizaciones de administrador mediante Microsoft Endpoint Configuration Manager (SCCM)](enabling-administrator-updates.md)** .  Las actualizaciones de Visual Studio se incluyen en el [Catálogo de Microsoft Update](https://www.catalog.update.microsoft.com/Home.aspx) y en [Windows Server Update Services (WSUS)](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus). Los administradores de empresa pueden descargar la actualización y distribuirla a las máquinas cliente de Visual Studio de la organización mediante herramientas de implementación estándar, como Microsoft Endpoint Configuration Manager (SCCM).

- **Comprender las opciones de implementación empresarial en entornos conectados en red**. La [guía del administrador de Visual Studio](visual-studio-administrator-guide.md) proporciona instrucciones basadas en escenarios para los administradores del sistema. 

- **[Obtener sugerencias para la solución de problemas](troubleshooting-installation-issues.md)** . Obtenga ayuda al instalar o actualizar Visual Studio y obtenga información sobre cómo informar de un problema si se le bloquea. Estas sugerencias incluyen instrucciones paso a paso que deberían resolver la mayoría de los problemas de instalación con conexión o sin conexión. 

- **[Crear una instalación sin conexión de Visual Studio](create-an-offline-installation-of-visual-studio.md)** . Si no tiene conexión a Internet o esta es limitada, busque opciones para instalar Visual Studio. 

- **[Crear paquetes de arranque](../deployment/creating-bootstrapper-packages.md)** . Obtenga información sobre cómo crear paquetes de arranque personalizados mediante la creación de manifiestos de productos y paquetes. 

- **[Aplicar automáticamente claves de producto durante la implementación de Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)** . Puede aplicar la clave de producto mediante programación como parte de un script que se usa para automatizar la implementación de Visual Studio. Se puede establecer una clave del producto en un dispositivo mediante programación durante una instalación de Visual Studio o después de completar una instalación. 

## <a name="install-visual-studio"></a>Instalar Visual Studio 

Obtenga información sobre cómo instalar Visual Studio en escenarios empresariales comunes. 

- **[Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)** . Use diversos parámetros para controlar o personalizar la instalación de Visual Studio. Automatice el proceso de instalación o cree una memoria caché de los archivos de instalación para su uso posterior. Para más información, consulte los [ejemplos de parámetros de línea de comandos](command-line-parameter-examples.md).

- **[Crear una instalación de red de Visual Studio](create-a-network-installation-of-visual-studio.md)** . Almacene en caché los archivos de la instalación inicial junto con todas las actualizaciones de producto en una única carpeta. 

- **[Instalar y usar Visual Studio y servicios de Azure detrás de un firewall o servidor proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)** . Si la organización usa medidas de seguridad, como un firewall o un servidor proxy, hay direcciones URL de dominio que quizá quiera agregar a una "lista de permitidos", así como puertos y protocolos que quiera abrir para tener la mejor experiencia posible a la hora de instalar y usar Visual Studio y los servicios de Azure. 

- **[Instalación de los certificados necesarios para la instalación sin conexión](../install/install-certificates-for-visual-studio-offline.md)** . Instale los certificados necesarios si la máquina cliente está completamente desconectada de Internet.

## <a name="update-visual-studio"></a>Actualizar Visual Studio 

Obtenga información sobre cómo actualizar Visual Studio correctamente y corregir problemas de actualización. 

- **[Aplicación de actualizaciones de administrador mediante Microsoft Endpoint Configuration Manager (SCCM)](../install/applying-administrator-updates.md)** . Aprenda a distribuir las actualizaciones de características, seguridad y calidad de Visual Studio mediante SCCM. 

- **[Actualizar una instalación basada en red de Visual Studio](update-a-network-installation-of-visual-studio.md)** . Actualice un diseño de instalación de red de Visual Studio con las actualizaciones de producto más recientes, de manera que se puede usar tanto como punto de instalación de la actualización más reciente de Visual Studio como para mantener instalaciones que ya están implementadas en estaciones de trabajo cliente.

- **[Actualizar Visual Studio mientras se encuentra en una base de referencia de mantenimiento](update-servicing-baseline.md)** . Comprenda el valor al actualizar en una base de referencia y aprenda la diferencia entre las versiones secundarias y las actualizaciones de mantenimiento. 

- **[Actualizar Visual Studio con un diseño sin conexión mínimo](update-minimal-layout.md)** . En el caso de los equipos que no están conectados a Internet, la creación de un diseño mínimo es la manera más fácil y rápida de actualizar las instancias de Visual Studio sin conexión.

- **[Reparar Visual Studio](repair-visual-studio.md) para corregir problemas de actualización**. En ocasiones, una instalación de Visual Studio resulta dañada. Una reparación es útil para corregir los problemas de tiempo de instalación en todas las operaciones de instalación, incluidas las actualizaciones. 

- **Seguir las [bases de referencia de seguridad de Windows](/windows/security/threat-protection/windows-security-baselines)** . Microsoft está dedicado a proporcionar a sus clientes sistemas operativos seguros, como Windows 10 y Windows Server, y aplicaciones seguras, como Microsoft Edge. Además del control de seguridad de sus productos, Microsoft también le permite tener un control preciso sobre los entornos, ya que proporciona diversas funciones de configuración. 

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Consulte también 

- [Guía de productividad para Visual Studio](../ide/productivity-features.md)

