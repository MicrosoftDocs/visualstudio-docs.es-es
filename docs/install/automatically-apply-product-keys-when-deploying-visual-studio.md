---
title: Aplicación automática de claves de producto
description: Obtenga información sobre cómo aplicar claves de producto mediante programación al implementar Visual Studio.
ms.date: 09/24/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d269102b4ab3edcf62a2101802c4731667b76eb7
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567208"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Aplicación automática de claves de producto durante la implementación de Visual Studio

Puede aplicar la clave de producto mediante programación como parte de un script que se usa para automatizar la implementación de Visual Studio. Se puede establecer una clave del producto en un dispositivo mediante programación durante una instalación de Visual Studio o después de completar una instalación.

## <a name="apply-the-license-after-installation"></a>Aplicar la licencia después de la instalación

::: moniker range="vs-2017"

Puede activar una versión instalada de Visual Studio con una clave de producto mediante la utilidad `StorePID.exe` en las máquinas de destino, en modo silencioso. `StorePID.exe` es un programa de utilidad que se instala con Visual Studio 2017 en la siguiente ubicación predeterminada: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

::: moniker-end

::: moniker range="vs-2019"

Puede activar una versión instalada de Visual Studio con una clave de producto mediante la utilidad `StorePID.exe` en las máquinas de destino, en modo silencioso. `StorePID.exe` es una utilidad que se instala con Visual Studio 2019 en la siguiente ubicación predeterminada: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE`

::: moniker-end

 Ejecute `StorePID.exe` con privilegios elevados, con un agente de System Center o un símbolo del sistema con privilegios elevados. Agregue la clave del producto y el código de producto de Microsoft (MPC).

>[!IMPORTANT]
> Asegúrese de incluir los guiones en la clave del producto.

 ```cmd
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker range="vs-2017"

En el ejemplo siguiente se muestra una línea de comandos para aplicar la licencia de Visual Studio 2017 Enterprise, que tiene un MPC de 08860, una clave de producto de `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` y presupone una ubicación de instalación predeterminada:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

En el ejemplo siguiente se muestra una línea de comandos para aplicar la licencia de Visual Studio 2019 Enterprise, que tiene un MPC de 09260, una clave de producto de `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` y presupone una ubicación de instalación predeterminada:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 En la siguiente tabla se muestran los códigos MPC de cada edición de Visual Studio:

| Edición de Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

::: moniker-end

::: moniker range="vs-2019"

| Edición de Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2019        | 09260 |
| Visual Studio Professional 2019      | 09262 |

::: moniker-end

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

> [!NOTE]
> Al ejecutar una instancia virtual de Visual Studio, asegúrese de que también virtualiza la carpeta AppData local y el Registro. Para solucionar problemas de instancias virtuales, ejecute `C:\Program Files (x86)\Microsoft Visual Studio\<version>\Common7\IDE\DDConfigCA.exe`.  

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalar Visual Studio](../install/install-visual-studio.md)
* [Crear una instalación sin conexión de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
