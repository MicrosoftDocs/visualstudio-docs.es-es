---
title: "Aplicación automática de claves de producto durante la implementación de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 08/14/2017
ms.reviewer: tims
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 4c50384f734f4162fa1cf482c563ed35a6622adb
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2017
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Aplicación automática de claves de producto durante la implementación de Visual Studio
Puede aplicar la clave de producto mediante programación como parte de un script que se usa para automatizar la implementación de Visual Studio. Se puede establecer una clave del producto en un dispositivo mediante programación durante una instalación de Visual Studio o después de completar una instalación.

## <a name="apply-the-license-after-installation"></a>Aplicar la licencia después de la instalación
 Puede activar una versión instalada de Visual Studio con una clave de producto mediante la utilidad `StorePID.exe` en las máquinas de destino, en modo silencioso. `StorePID.exe` es un programa de utilidad que se instala con Visual Studio 2017 en la siguiente ubicación predeterminada: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 Ejecute `StorePID.exe` con privilegios elevados, con un agente de System Center o un símbolo del sistema con privilegios elevados. Agregue la clave del producto y el código de producto de Microsoft (MPC).

>[!IMPORTANT]
> Asegúrese de incluir los guiones en la clave del producto.

 ```
 StorePID.exe [product key including the dashes] [MPC]
 ```

 En el ejemplo siguiente se muestra una línea de comandos para aplicar la licencia de Visual Studio 2017 Enterprise, que tiene un MPC de 08860, una clave de producto de `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` y presupone una ubicación de instalación predeterminada:

 ```cmd
 "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 En la siguiente tabla se muestran los códigos MPC de cada edición de Visual Studio:

| Edición de Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

Si `StorePID.exe` aplica correctamente la clave de producto, devuelve un valor `%ERRORLEVEL%` de 0. Si se encuentran errores, devuelve uno de los códigos siguientes, dependiendo de la condición de error:

| Error                     | Código |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

## <a name="get-support"></a>Obtener soporte técnico
En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017). Si ninguno de los pasos de solución de problemas ayuda, puede ponerse en contacto con nosotros por chat para obtener asistencia para la instalación (solo en inglés). Para más información, consulte la [página de soporte técnico de Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:
* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/), y hacer preguntas y encontrar respuestas.
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de nuestra [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también
 * [Instalar Visual Studio](../install/install-visual-studio.md)
 * [Crear una instalación sin conexión de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
