---
title: "Aplicación automática de claves de producto durante la implementación de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
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
ms.openlocfilehash: 493ea235a3d89a04a4c6accfa491e622792e4397
ms.contentlocale: es-es
ms.lasthandoff: 05/09/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Aplicación automática de claves de producto durante la implementación de Visual Studio
Puede aplicar la clave de producto mediante programación como parte de un script usado para automatizar la implementación de Visual Studio. Las claves de producto se pueden establecer en un dispositivo mediante programación durante la instalación de Visual Studio o después de completar una instalación.

## <a name="apply-the-license-after-installation"></a>Aplicar la licencia después de la instalación
 Puede activar una versión instalada de Visual Studio con una clave de producto mediante la utilidad `StorePID.exe` en las máquinas de destino en modo silencioso. `StorePID.exe` es un programa de utilidad que se instala con Visual Studio 2017 en la siguiente ubicación predeterminada: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 Ejecute `StorePID.exe` con privilegios elevados, ya sea mediante un agente de System Center o un símbolo del sistema con privilegios elevados, seguido de la clave de producto (incluidos los guiones) y el código de producto de Microsoft (MPC). Asegúrese de incluir los guiones en la clave del producto.

 ```
 StorePID.exe [product key including the dashes] [MPC]
 ```

 Este es un ejemplo de línea de comandos para aplicar la licencia de Visual Studio 2017 Enterprise, que tiene un MPC de 08860, con una clave de producto `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, suponiendo su instalación en una ubicación predeterminada:

 ```cmd
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 En la siguiente tabla se muestran los códigos MPC de cada edición de Visual Studio:

| Edición de Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

Si `StorePID.exe` aplicó correctamente la clave de producto, se devolverá 0 en `%ERRORLEVEL%`. Si se encuentran errores, se devolverá un código según la condición de error:

| Error                     | Código |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

## <a name="see-also"></a>Vea también
 * [Instalar Visual Studio](../install/install-visual-studio.md)
 * [Crear una instalación sin conexión de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)

