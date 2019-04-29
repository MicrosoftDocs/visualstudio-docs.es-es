---
title: Importación o exportación de configuraciones de instalación
titleSuffix: ''
description: Obtenga información sobre cómo usar la característica de importación o exportación de la configuración en Visual Studio
ms.date: 04/19/2019
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- import installation configuration
- export installation configuration
- install Visual Studio
- Visual Studio installer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: facbbf5903d683ea3a13bdd875dfe2b6c63b6367
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786402"
---
# <a name="import-or-export-installation-configurations"></a>Importación o exportación de configuraciones de instalación

Puede configurar Visual Studio en toda la organización con un archivo de configuración de instalación. Para hacerlo, simplemente exporte la información de componentes y la carga de trabajo a un archivo .vsconfig mediante el instalador de Visual Studio. Luego puede importar la configuración a instalaciones nuevas o existentes.

Esta es la manera de hacerlo.

::: moniker range="vs-2017"

> [!NOTE]
> Esta funcionalidad está disponible solo en la versión 15.9 y posteriores de Visual Studio 2017.

::: moniker-end

## <a name="export-a-configuration"></a>Exportación de una configuración

Puede elegir exportar un archivo de configuración de instalación ya sea desde una instancia de Visual Studio instalada anteriormente o desde una que esté instalando en este momento.

1. Abra el instalador de Visual Studio.

1. En la tarjeta del producto, elija el botón **Más** y seleccione **Exportar configuración**.

   ![Exportación de configuración desde la tarjeta del producto en el instalador de Visual Studio](../install/media/vs-2019/vs-installer-export-config.png)

1. Busque o escriba la ubicación donde quiere guardar el archivo .vconfig y elija **Revisar detalles**.

   ![Exportación de configuración desde el instalador de Visual Studio](../install/media/vs-2019/export-configuration-confirmation.png)

1. Asegúrese de tener las cargas de trabajo y los componentes que desea y elija **Exportar**.

## <a name="import-a-configuration"></a>Importación de una configuración

Cuando esté listo para importar un archivo de configuración de instalación, siga estos pasos.

1. Abra el instalador de Visual Studio.

1. En la tarjeta del producto, elija el botón **Más** y seleccione **Importar configuración**.

1. Busque el archivo .vconfig que quiere importar y elija **Revisar detalles**.

1. Asegúrese de tener las cargas de trabajo y los componentes que desea y elija **Cerrar**.

::: moniker range="vs-2019"

## <a name="automatically-install-missing-components"></a>Instalación automática de los componentes faltantes

**Novedades de Visual Studio 2019**: Cuando guarda un archivo .vsconfig en el directorio raíz de la solución y luego abre una solución, Visual Studio detecta automáticamente los componentes que faltan y le pregunta si quiere instalarlos.

![El Explorador de soluciones sugiere componentes adicionales](../install/media/vs-2019/solution-explorer-config-file.png)

También puede generar un archivo .vsconfig directamente desde el Explorador de soluciones.

1. Haga clic con el botón derecho en el archivo de la solución.

1. Elija **Agregar** > **Archivo de configuración de instalación**.

1. Confirme la ubicación donde quiere guardar el archivo .vsconfig y luego elija **Revisar detalles**.

1. Asegúrese de tener las cargas de trabajo y los componentes que desea y elija **Exportar**.

::: moniker-end

> [!NOTE]
> Para más información, consulte la entrada de blog [Configure Visual Studio across your organization with .vsconfig](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/) (Configuración de Visual Studio en toda la organización con .vsconfig).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Creación de una instalación de red de Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Actualizar una instalación basada en red de Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Controlar las actualizaciones a implementaciones de Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Set defaults for enterprise deployments](set-defaults-for-enterprise-deployments.md)(Establecimiento de valores predeterminados para implementaciones de empresa)
