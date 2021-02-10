---
title: Reparación de Visual Studio.
titleSuffix: ''
description: Obtenga información sobre cómo reparar una instalación de Visual Studio 2017
ms.date: 10/12/2020
ms.custom: seodec18
ms.topic: how-to
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 09f167866d03b29530f4845aa958198215289555
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959303"
---
# <a name="repair-visual-studio"></a>Repare Visual Studio.

En ocasiones, una instalación de Visual Studio resulta dañada. Una reparación es útil para corregir los problemas de tiempo de instalación en todas las operaciones de instalación, incluidas las actualizaciones.

## <a name="when-to-use-repair"></a>Cuándo usar la reparación
* Si tiene problemas de carga útil con la instalación. Esto puede ocurrir cuando la escritura del archivo en el disco no se realiza correctamente y no se puede corregir eliminando el archivo dañado. La reparación puede volver a adquirir los archivos necesarios. 
* Si tiene problemas de descarga del lado cliente. Suponiendo que ha resuelto cualquier problema de conexión o proxy, la reparación puede ser útil. 
* Si tiene problemas para actualizar Visual Studio. La reparación corrige muchos problemas comunes de actualización. 

> [!TIP] 
> Si el problema de instalación se debe a un problema en un servicio de Windows subyacente, como Windows Installer, es posible que la reparación se tope con el mismo problema. Entre otras causas, los problemas sistémicos pueden deberse a un servicio Windows Installer roto o a una conexión a Internet inestable. Para comprobar si hay un problema sistémico, use el informe de errores generado a partir de la operación de instalación.

> [!NOTE] 
> La reparación de Visual Studio restablece la configuración del usuario y vuelve a instalar los ensamblados que ya tiene. Si experimenta un problema con el producto, cree un [vale de comentarios de Visual Studio](https://aka.ms/feedback/suggest?space=8), ya que es posible que la reparación no resuelva el problema.

## <a name="how-to-repair"></a>Reparación
::: moniker range="vs-2017"

1. Busque el **instalador de Visual Studio** en su equipo.

     Por ejemplo, en un equipo que ejecuta la Actualización de aniversario de Windows 10 o posterior, seleccione **Iniciar** y, después, desplácese hasta la letra **V** donde lo verá como **Instalador de Visual Studio**.

   > [!NOTE]
   > En algunos equipos, el instalador de Visual Studio podría aparecer en la letra **"M"** como **Microsoft Visual Studio Installer** (instalador de Microsoft Visual Studio).
   >
   > Como alternativa, puede encontrar el Instalador de Visual Studio en la siguiente ubicación: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Abra el instalador, elija **Más** y, luego, **Reparar**.

    ![Reparación de Visual Studio desde el instalador de Visual Studio](media/repair-visual-studio.png "Reparación de Visual Studio desde el instalador de Visual Studio")

   > [!NOTE]
   > Al reparar Visual Studio, se restablece el entorno. Se eliminan las personalizaciones locales, como las extensiones por usuario instaladas sin elevación, la configuración de usuario y los perfiles. La configuración sincronizada, como temas, colores o enlaces de teclado, se restaura.
   >

   > [!TIP]
   > La opción **Reparar** solo se muestra para las instancias instaladas de Visual Studio. Si no ve la opción **Reparar**, es posible que haya seleccionado **Más** en una versión mostrada en el instalador de Visual Studio como "Disponible", en lugar de "Instalada".

::: moniker-end

::: moniker range="vs-2019"

1. Busque el **instalador de Visual Studio** en su equipo.

     En el menú Inicio de Windows, puede buscar "instalador".

     ![Instalador de Visual Studio](media/vs-2019/visual-studio-installer.png "Búsqueda del Instalador de Visual Studio")

     > [!NOTE]
     > También pude encontrar el instalador de Visual Studio en la siguiente ubicación:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Es posible que tenga que actualizar el instalador antes de continuar. De ser así, siga las indicaciones.

1. En el instalador, busque la edición de Visual Studio que tenga instalada. A continuación, elija **Más** y, luego, **Reparar**.

     ![Reparación de Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Reparación de Visual Studio 2019")

   > [!NOTE]
   > Al reparar Visual Studio, se restablece el entorno. Se eliminan las personalizaciones locales, como las extensiones por usuario instaladas sin elevación, la configuración de usuario y los perfiles. La configuración sincronizada, como temas, colores o enlaces de teclado, se restaura.
   >

   > [!TIP]
   > La opción **Reparar** solo se muestra para las instancias instaladas de Visual Studio. Si no ve la opción **Reparar**, es posible que haya seleccionado **Más** en una versión mostrada en el instalador de Visual Studio como "Disponible", en lugar de "Instalada".

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalar Visual Studio](install-visual-studio.md)
* [Actualizar Visual Studio](update-visual-studio.md)
* [Desinstalar Visual Studio](uninstall-visual-studio.md)
* [Solución de problemas de instalación y actualización de Visual Studio](troubleshooting-installation-issues.md)
