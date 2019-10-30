---
title: Actualización de Visual Studio mientras se encuentra en una base de referencia de mantenimiento
description: Aprenda a actualizar Visual Studio mientras se encuentra en una línea de base de mantenimiento.
ms.date: 07/17/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: doughall
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 4e84704d4ca37dd9e36da3838b5b1b23f068568c
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888575"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Actualización de Visual Studio mientras se encuentra en una base de referencia de mantenimiento

A lo largo de su ciclo de vida, Visual Studio se actualiza con frecuencia. Hay dos tipos de actualizaciones: 

* **Actualizaciones de versión secundaria**, por ejemplo, de 16.0 a 16.1, que incluyen nuevas características y componentes.  
* **Actualizaciones de mantenimiento**, por ejemplo, de 16.0.4 a 16.0.5, que incluyen solo correcciones para problemas críticos.

Los administradores de empresa pueden elegir mantener sus clientes en una línea base de mantenimiento. Tras la publicación de una línea base de mantenimiento, es posible aplicar la anterior con las actualizaciones de mantenimiento durante un año.

La opción de línea base de mantenimiento concede más flexibilidad a los desarrolladores y administradores para adoptar las nuevas características, las correcciones de errores o los componentes incluidos en las nuevas actualizaciones menores. La primera línea de base de mantenimiento es 16.0.x. Para obtener más información, vea [Opciones de soporte técnico para clientes de las versiones Enterprise y Professional](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers).

## <a name="how-to-get-onto-a-servicing-baseline"></a>Incorporación a una línea de base de mantenimiento

Para empezar a usar una línea base de mantenimiento, descargue un programa previo del Instalador de Visual Studio de versión no editable, disponible en [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). Los programas previos tienen vínculos a las configuraciones de los productos, las cargas de trabajo y los componentes de esa versión específica.

> [!NOTE]
> Asegúrese de distinguir entre el programa previo de versión no editable y los programas previos estándares. Los programas previos estándares están configurados para usar la versión más reciente de Visual Studio. Los programas previos estándares tienen un número en el nombre de archivo (por ejemplo, vs_enterprise__123456789-123456789.exe) cuando se descargan de My.VisualStudio.com.

Durante la instalación, los administradores de empresa deben configurar sus clientes para impedir que se actualicen a la versión más reciente. Existen varias formas de hacerlo:
- Puede [cambiar la opción `channelUri` del archivo de configuración de respuesta](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network) para que se use un manifiesto de canal en el diseño o la carpeta local.
- Puede [modificar el valor channelUri mediante la ejecución de la línea de comando](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet) para que se use un archivo que no exista.
- Puede [establecer directivas en el sistema cliente para deshabilitar las actualizaciones](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating), de modo que los clientes no puedan realizar la actualización ellos mismos.

### <a name="install-a-servicing-baseline-on-a-network"></a>Instalación de una línea de base de mantenimiento en una red

Los administradores que usen una instalación de diseño en red deben modificar el valor `channelUri` en el archivo *response.json* del diseño para usar el archivo *channelmanifest.json*, que se encuentra en la misma carpeta. Para conocer los pasos necesarios, vea [Control de actualizaciones a implementaciones de Visual Studio basadas en red](controlling-updates-to-visual-studio-deployments.md). El cambio del valor `channelUri` permite a los clientes buscar actualizaciones en la ubicación del diseño.

### <a name="install-a-servicing-baseline-via-the-internet"></a>Instalación de una línea de base de mantenimiento en Internet

En el caso de una instalación basada en Internet, agregue `--channelUri` con un manifiesto de canal inexistente en la línea de comandos utilizada para iniciar el programa de instalación. De este modo, Visual Studio no usa la versión más reciente disponible de una actualización. Por ejemplo:

```cmd
vs_enterprise.exe --channelUri c:\doesnotexist.chman
```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>Uso de la configuración de directiva para evitar que los clientes se actualicen

Otra opción para controlar las actualizaciones en un cliente es [desactivar las notificaciones de actualización](controlling-updates-to-visual-studio-deployments.md). Use esta opción si no se ha cambiado el valor de channelUri en la instalación. De este modo, el cliente no recibirá vínculos a la versión más reciente disponible. Sigue siendo necesario un programa previo de versión no editable para realizar la actualización a una versión específica en el cliente.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Continuidad en una línea de base de mantenimiento

Cuando hay una actualización para una línea base de mantenimiento, se publican los archivos del programa previo de versión no editable para la actualización de mantenimiento en [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0).

En el caso de los administradores que implementan mediante una instalación de diseño en red, el administrador debe actualizar la [ubicación del diseño](update-a-network-installation-of-visual-studio.md). Los clientes que instalaron desde la ubicación recibirán notificaciones de actualización. Si la actualización debe implementarse en los clientes, siga [estas instrucciones](update-a-network-installation-of-visual-studio.md#how-to-deploy-an-update-to-client-machines). Si modifica el archivo "response.json" de una actualización, no agregue más cargas de trabajo, componentes ni lenguajes. La administración de esta configuración debe realizarse como una implementación de tipo "modify" después de actualizar el producto.

En el caso de una instalación basada en Internet, ejecute el nuevo programa previo de versión no editable con el parámetro `--channelUri` que apunte a un manifiesto de canal no existente en el cliente. Si la actualización se implementa en modo silencioso o pasivo, use dos comandos independientes:

1. Actualice el instalador de Visual Studio:

    ```cmd
    vs_enterprise.exe --quiet --update
    ```

2. Actualice la propia aplicación de Visual Studio:

    ```cmd
    vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalar Visual Studio](install-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Herramientas para detectar y administrar instancias de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Definición de la configuración en un archivo de respuesta](automated-installation-with-response-file.md)
* [Control updates to network-based Visual Studio deployments](controlling-updates-to-visual-studio-deployments.md) (Control de actualizaciones de implementaciones de Visual Studio basadas en red)
* [Ciclo de vida y mantenimiento del producto de Visual Studio](/visualstudio/releases/2019/servicing/)
