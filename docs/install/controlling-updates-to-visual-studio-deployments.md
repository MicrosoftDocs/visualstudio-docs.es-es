---
title: Control de actualizaciones a implementaciones de Visual Studio | Microsoft Docs
description: "{{MARCADOR DE POSICIÓN}}"
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 2e68d084c88c398d1576f53a79a156c111651895
ms.contentlocale: es-es
ms.lasthandoff: 05/09/2017

---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Control de actualizaciones a implementaciones de Visual Studio basadas en red

Con frecuencia, los administradores de empresa crean un diseño y lo hospedan en un recurso compartido de red para la implementación en sus usuarios finales.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Control de dónde Visual Studio busca actualizaciones
De forma predeterminada, Visual Studio continuará buscando actualizaciones en línea, incluso si la instalación se ha implementado desde un recurso compartido de red. Si hay disponible una actualización, el usuario podrá instalarla; cualquier contenido actualizado que no se encuentre en el diseño sin conexión se descargará desde la Web.

Si desea un control directo sobre dónde Visual Studio busca actualizaciones, así como de las versiones a las que se actualizan sus usuarios, puede modificar la ubicación en la que Visual Studio busca actualizaciones mediante estos pasos:

 1. Cree un diseño sin conexión:
    ```
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```
 2. Cópielo en el recurso compartido de archivos donde desea hospedarlo:
    ```
    xcopy /e C:\vs2017offline \\server\share\VS2017
    ```
 3. Modifique el archivo response.json en el diseño y cambiar el valor `channelUri` para que apunte a una copia del archivo channelManifest.json que controla el administrador. <b>Nota:</b> Asegúrese de usar caracteres de escape de barra diagonal en el valor, de este modo:
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 4. Ahora los usuarios finales pueden ejecutar la instalación de Visual Studio desde este recurso compartido.
    ```
    \\server\share\VS2017\vs_enterprise.exe
    ```
 5. Cuando un administrador de empresa determina que es hora de que sus usuarios actualicen a una nueva versión de Visual Studio, pueden [actualizar la ubicación del diseño](update-a-network-installation-of-visual-studio.md) para incorporar los archivos actualizados, con un comando similar al siguiente:
    ```
    vs_enterprise.exe --layout \\server\share\VS2017 --lang en-US
    ```
 6. Asegúrese de que el archivo response.json en el diseño actualizado todavía contenga sus personalizaciones, en concreto la modificación de channelUri:
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 7. Las instalaciones existentes de Visual Studio de este diseño buscarán actualizaciones en `\\server\share\VS2017\ChannelManifest.json`. Si este archivo channelManifest.json es más reciente que el que ha instalado el usuario, Visual Studio notificará al usuario que hay una actualización disponible.
 8. Las nuevas instalaciones instalarán automáticamente la versión actualizada de Visual Studio directamente desde el diseño.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Control de notificaciones en el IDE de Visual Studio
Como se describió anteriormente, Visual Studio comprueba la ubicación desde la que se ha instalado (por ejemplo, el recurso compartido de red o Internet), para ver si hay actualizaciones disponibles. Cuando hay una actualización disponible, Visual Studio lo notifica al usuario de forma predeterminada con una marca de notificación en la esquina superior derecha de la ventana: ![marca de notificación de actualizaciones](~/docs/install/media/notification-flag.png)

Si no desea que los usuarios finales reciban notificaciones de actualizaciones (por ejemplo, las actualizaciones se proporcionan a través de un mecanismo central de distribución de software), puede deshabilitar estas notificaciones.

Dado que Visual Studio 2017 [almacena las entradas del Registro en un Registro privado](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), no puede modificar directamente el Registro de la manera normal. Sin embargo, Visual Studio incluye un comando `vsregedit.exe` que puede usar para cambiar la configuración de dicha aplicación. Puede desactivar las notificaciones con el siguiente comando:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2 dword 0
```

Reemplace el directorio del comando anterior para que coincida con la instancia instalada que desee editar. 

> [!TIP]
> Use [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) para buscar una instancia específica de Visual Studio en una estación de trabajo cliente. 

## <a name="see-also"></a>Vea también
* [Instalar Visual Studio](install-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Herramientas para administrar instancias de Visual Studio](tools-for-managing-visual-studio-instances.md)

