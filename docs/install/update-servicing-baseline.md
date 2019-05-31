---
title: Actualización de Visual Studio mientras se encuentra en una base de referencia de mantenimiento
titleSuffix: ''
description: Aprenda a actualizar Visual Studio mientras se encuentra en una línea de base de mantenimiento.
ms.date: 05/22/2019
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
ms.openlocfilehash: 8928feffed77f8bfbb3787bd9a20737b9c7b3f9e
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2019
ms.locfileid: "66213786"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Actualización de Visual Studio mientras se encuentra en una base de referencia de mantenimiento

Visual Studio 2019 tendrá actualizaciones frecuentes durante su [ciclo de vida del producto](/visualstudio/productinfo/release-rhythm.md#release-channel-updates). Esto incluirá tanto actualizaciones menores de las versiones (por ejemplo: de 16.0 a 16.1) que pueden incluir nuevas características y componentes, y actualizaciones de mantenimiento (por ejemplo: de 16.0.4 a 16.0.5) que contienen solo correcciones destinadas a resolver problemas críticos. 

Los administradores de empresas puede optar por mantener a sus clientes en una línea de base de mantenimiento, que es compatible con las actualizaciones de mantenimiento durante un año después de la publicación de la siguiente línea de base de mantenimiento. Esto concede más flexibilidad a los desarrolladores y administradores para adoptar las nuevas características, las correcciones de errores o los componentes incluidos en las nuevas actualizaciones menores. La primera línea de base de mantenimiento es 16.0.x. Consulte [Opciones de soporte técnico para clientes de las versiones Enterprise y Professional](/visualstudio/releases/2019/servicing.md#support-options-for-enterprise-and-professional-customers) para obtener más información.

## <a name="how-to-get-onto-a-servicing-baseline"></a>Incorporación a una línea de base de mantenimiento

Para empezar a usar una línea de base de mantenimiento, descargue un programa previo del Instalador de Visual Studio de versión no editable en [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). Estos programas previos tienen vínculos a las configuraciones de productos, las cargas de trabajo y los componentes para esa versión específica. 

> [!NOTE]
> Asegúrese de distinguir entre el programa previo de versión no editable y los programas previos normales. Los programas previos normales están configurados para usar la versión más reciente de Visual Studio. Tienen un número en el nombre de archivo (por ejemplo: vs_enterprise__123456789 123456789.exe) cuando se descargan desde my.visualstudio.com.

Durante la instalación, los administradores de la organización deben configurar sus clientes para impedir que se actualicen a la versión más reciente. Esto puede hacerse [cambiando el valor de channelUri en el archivo de configuración de la respuesta](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network) para usar un manifiesto del canal en la carpeta de diseño o local, [modificando el valor de channelUri a través de la ejecución de la línea de comandos](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet) para usar un archivo inexistente o [configurando directivas en el sistema cliente para deshabilitar las actualizaciones](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating) a fin de impedir que los clientes se actualicen por sí mismos. 

### <a name="install-a-servicing-baseline-on-a-network"></a>Instalación de una línea de base de mantenimiento en una red

En el caso de los administradores que usan una instalación de diseño de red, modifique el valor de channelUri en `response.json` en el diseño para utilizar el archivo channelmanifest.json que se encuentra en la misma carpeta. Consulte [Control de actualizaciones a implementaciones de Visual Studio basadas en red](controlling-updates-to-visual-studio-deployments.md) para obtener instrucciones paso a paso. El cambio del valor de channelUri permite a los clientes buscar actualizaciones en la ubicación del diseño. 

### <a name="install-a-servicing-baseline-via-the-internet"></a>Instalación de una línea de base de mantenimiento en Internet

Si es una instalación basada en internet, agregue `--channelUri` con un manifiesto de canal inexistente en la línea de comandos utilizada para iniciar el programa de instalación. De este modo, Visual Studio no usa la versión más reciente disponible de una actualización. A continuación se muestra un ejemplo:

  ```cmd
   vs_enterprise.exe --channelUri c:\doesnotexist.chman 
  ```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>Uso de la configuración de directiva para evitar que los clientes se actualicen

Otra opción para controlar las actualizaciones en un cliente es [desactivar las notificaciones de actualización](controlling-updates-to-visual-studio-deployments.md). Use esta opción si no se ha cambiado el valor de channelUri en la instalación. De este modo, el cliente no recibirá vínculos a la versión más reciente disponible. Un programa previo de versión no editable sigue siendo necesario para actualizar a una versión específica en el cliente.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Continuidad en una línea de base de mantenimiento

Cuando hay una actualización para una línea de base de mantenimiento, se publican los archivos del programa previo de versión no editable para la actualización de mantenimiento en [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). Estos pueden usarse en varios escenarios.

En el caso de los administradores que implementan mediante una instalación de diseño en red, el administrador querrá actualizar la [ubicación del diseño](update-a-network-installation-of-visual-studio.md). Los clientes que instalaron desde la ubicación recibirán notificaciones de actualización. Si la actualización debe implementarse en los clientes, siga [estas instrucciones](update-a-network-installation-of-visual-studio.md#how-to-deploy-an-update-to-client-machines). Cuando se modifica el archivo "response.json" para una actualización, no agregue más cargas de trabajo, componentes o lenguajes. La administración de esta configuración debe realizarse como una implementación de tipo "modify" después de actualizar el producto. 

Si es una instalación basada en Internet, ejecute el nuevo programa previo de versión no editable con el parámetro `--channelUri` que apunta a un manifiesto de canal no existente en el cliente. Si la actualización se implementa en modo silencioso o pasivo, use dos comandos independientes:

1. En primer lugar, actualice el instalador de Visual Studio: <br>```vs_enterprise.exe --quiet --update```
2. Luego, actualice la propia aplicación de Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalar Visual Studio](install-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Herramientas para detectar y administrar instancias de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Definición de la configuración en un archivo de respuesta](automated-installation-with-response-file.md)
* [Control updates to network-based Visual Studio deployments](controlling-updates-to-visual-studio-deployments.md) (Control de actualizaciones de implementaciones de Visual Studio basadas en red)
* [Ciclo de vida y mantenimiento del producto de Visual Studio](/visualstudio/releases/2019/servicing/)
