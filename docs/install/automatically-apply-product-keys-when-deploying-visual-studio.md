---
title: Aplicación automática de claves de producto
description: Obtenga información sobre cómo aplicar claves de producto mediante programación al implementar Visual Studio.
ms.date: 09/24/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a78da89d8e8ce4251bc9288270628bfe784eca7a
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307726"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Aplicación automática de claves de producto durante la implementación de Visual Studio

Puede aplicar la clave de producto mediante programación como parte de un script que se usa para automatizar la implementación de Visual Studio. Se puede establecer una clave del producto en un dispositivo mediante programación durante una instalación de Visual Studio o después de completar una instalación.

::: moniker range=">=vs-2022"

> [!IMPORTANT]
> Visual Studio 2022 se encuentra actualmente en versión preliminar y, durante este período, está disponible con una licencia de evaluación para la que no es necesario aplicar la clave de producto.

::: moniker-end

::: moniker range="vs-2017"

## <a name="apply-the-license-after-installation"></a>Aplicar la licencia después de la instalación

Puede activar una versión instalada de Visual Studio con una clave de producto mediante la utilidad `StorePID.exe` en las máquinas de destino, en modo silencioso. `StorePID.exe` es un programa de utilidad que se instala con Visual Studio 2017 en la siguiente ubicación predeterminada:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE
```

 Ejecute `StorePID.exe` con privilegios elevados, con un agente de System Center o un símbolo del sistema con privilegios elevados. Agregue la clave del producto y el código de producto de Microsoft (MPC).

>[!IMPORTANT]
> Asegúrese de incluir los guiones en la clave del producto.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2019"

## <a name="apply-the-license-after-installation"></a>Aplicar la licencia después de la instalación

Puede activar una versión instalada de Visual Studio con una clave de producto mediante la utilidad `StorePID.exe` en las máquinas de destino, en modo silencioso. `StorePID.exe` es una utilidad que se instala con Visual Studio 2019 en la siguiente ubicación predeterminada:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE
```

 Ejecute `StorePID.exe` con privilegios elevados, con un agente de System Center o un símbolo del sistema con privilegios elevados. Agregue la clave del producto y el código de producto de Microsoft (MPC).

>[!IMPORTANT]
> Asegúrese de incluir los guiones en la clave del producto.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2017"

En el ejemplo siguiente se muestra una línea de comandos para aplicar la licencia de Visual Studio 2017 Enterprise, que tiene un MPC de 08860, una clave de producto de `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` y presupone una ubicación de instalación predeterminada:

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

En el ejemplo siguiente se muestra una línea de comandos para aplicar la licencia de Visual Studio 2019 Enterprise, que tiene un MPC de 09260, una clave de producto de `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` y presupone una ubicación de instalación predeterminada:

```shell
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

::: moniker range="vs-2017"

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
> Al ejecutar una instancia virtual de Visual Studio, asegúrese de que también virtualiza la carpeta AppData local y el Registro. Para solucionar problemas de instancias virtuales, ejecute `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe`.  

::: moniker-end

::: moniker range="vs-2019"

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
> Al ejecutar una instancia virtual de Visual Studio, asegúrese de que también virtualiza la carpeta AppData local y el Registro. Para solucionar problemas de instancias virtuales, ejecute `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe`.  

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalación de Visual Studio](../install/install-visual-studio.md)
* [Crear una instalación sin conexión de Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)