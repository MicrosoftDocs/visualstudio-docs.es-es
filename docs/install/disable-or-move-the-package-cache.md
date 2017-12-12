---
title: "Deshabilitación o traslado de la caché de paquetes | Microsoft Docs"
description: "Deshabilite, habilite o mueva la caché de paquetes para las implementaciones de Visual Studio."
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: heaths
ms.author: heaths
manager: ghogen
ms.openlocfilehash: f279a97cc91aa2ed3fa2efe5df21aaa90ddc5271
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2017
---
# <a name="disable-or-move-the-package-cache"></a>Deshabilitación o traslado de la caché de paquetes

La caché de paquetes proporciona un origen de paquetes instalados en caso de que tenga que reparar Visual Studio u otros productos relacionados cuando no disponga de conexión a Internet. Sin embargo, es posible que con algunas unidades de disco o instalaciones de sistemas, no pueda conservar todos esos paquetes.
El instalador los descargará cuando sea necesario; así que si quiere guardar o recuperar espacio en disco, puede deshabilitar o mover la caché de paquetes.

## <a name="disable-the-package-cache"></a>Deshabilitación de la caché de paquetes

Antes de instalar, modificar o reparar Visual Studio u otros productos con el nuevo instalador, puede iniciar el instalador pasándole el modificador `--nocache`.

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Cualquier operación que realice en cualquier producto quitará los paquetes existentes para ese producto y evitará que se guarde ningún paquete después de que se ha instalado. Si modifica o repara Visual Studio y se necesitan paquetes, se descargarán automáticamente y se quitarán una vez instalados.

Si desea volver a habilitar la caché, pase en su lugar `--cache`. Solo se almacenan en caché los paquetes necesarios, así que si tiene que restaurar todos los paquetes, debe reparar Visual Studio antes de desconectarse de la red.

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

También puede configurar la [directiva del Registro](set-defaults-for-enterprise-deployments.md) `KeepDownloadedPayloads` para deshabilitar la caché antes de instalar, modificar o reparar Visual Studio.

## <a name="move-the-package-cache"></a>Traslado de la caché de paquetes

Una configuración común del sistema es tener instalado Windows en una SSD con uno o varios discos duros más grandes pensando en las necesidades de desarrollo, como el código fuente, los archivos binarios del programa, etc. Si, por el contrario, desea trabajar sin conexión, puede mover la caché de paquetes.

Actualmente, esto solo lo hace si configura la [directiva del Registro](set-defaults-for-enterprise-deployments.md) `CachePath` antes de instalar, modificar o reparar Visual Studio.

## <a name="get-support"></a>Obtener soporte técnico
En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017). Si ninguno de los pasos de solución de problemas ayuda, puede ponerse en contacto con nosotros por chat para obtener asistencia para la instalación (solo en inglés). Para más información, consulte la [página de soporte técnico de Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:
* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/), y hacer preguntas y encontrar respuestas.
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de nuestra [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también

 * [Instalar Visual Studio](install-visual-studio.md)
 * [Set defaults for enterprise deployments](set-defaults-for-enterprise-deployments.md)(Establecimiento de valores predeterminados para implementaciones de empresa)
 * [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
