---
title: Configuración de confianza de archivos y carpetas
description: Obtenga información sobre cómo cambiar la configuración de confianza de archivos y carpetas para proteger Visual Studio.
author: 2percentsilk
ms.author: allisb
ms.date: 09/05/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.PathTrustOptions
helpviewer_keywords:
- file security
- folder security
- mark of the web
- trusted files
- trusted folders
ms.openlocfilehash: 492a94962d255a9d18dcabdababf7fa6a540ada1
ms.sourcegitcommit: 935e1388281df0f04147802606b5cb7f513d45ed
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2020
ms.locfileid: "88197395"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Configurar la confianza de archivos y carpetas

Visual Studio pide la aprobación del usuario antes de abrir los proyectos que tengan la [marca de la web](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85)). Para mayor seguridad, también puede configurar Visual Studio para que solicite la aprobación del usuario antes de abrir cualquier archivo o carpeta que tenga la marca del atributo de web o que no se designe como *de confianza*. Las comprobaciones de los archivos y las carpetas están deshabilitadas de forma predeterminada.

> [!WARNING]
> Debería asegurarse de que el archivo, la carpeta o la solución procede de una persona o una ubicación de confianza antes de aprobarlos.

## <a name="configure-trust-settings"></a>Definir la configuración de confianza

Para cambiar la configuración de confianza, siga estos pasos:

1. Abra **Herramientas** > **Opciones** > **Configuración de confianza** y seleccione el vínculo **Definir la configuración de confianza** en el panel derecho.

2. Elija el nivel de comprobaciones que quiere para los archivos y las carpetas. Puede tener diferentes comprobaciones para cada uno de ellos. Las opciones son:

   * **Sin comprobación**: Visual Studio no realiza ninguna comprobación.

   * **Comprobar la marca del atributo de web**: si el archivo o la carpeta tiene la marca del atributo de web, Visual Studio se bloquea y solicita permiso para abrirlo.

   * **Comprobar si la ruta de acceso es de confianza**: si el archivo o la carpeta no forma parte de la lista **Rutas de acceso de confianza**, Visual Studio se bloquea y solicita permiso para abrirlo.

   ![Opciones de comprobación de confianza](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Agregar rutas de acceso de confianza

Para agregar rutas de acceso de confianza, siga estos pasos:

1. Abra **Herramientas** > **Opciones** > **Configuración de confianza** y seleccione el vínculo **Definir la configuración de confianza** en el panel derecho.

2. Haga clic en **Agregar** en el cuadro de diálogo **Configuración de confianza** y después seleccione **Archivo** o **Carpeta**.

3. Vaya al archivo o la carpeta que quiera agregar a la lista de confianza y selecciónelo.

   La ruta de acceso al archivo o la carpeta aparece en la lista **Rutas de acceso de confianza**.

   ![Rutas de acceso de confianza agregadas](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Eliminar rutas de acceso de confianza

Para eliminar rutas de acceso de confianza, siga estos pasos:

1. Abra **Herramientas** > **Opciones** > **Configuración de confianza** y seleccione el vínculo **Definir la configuración de confianza** en el panel derecho.

2. Seleccione la ruta de acceso que quiera quitar de la lista **Rutas de acceso de confianza** y luego haga clic en **Quitar**.

   > [!TIP]
   > Para seleccionar varias entradas, mantenga presionada la tecla **Mayús** mientras selecciona las rutas de acceso.

   Las rutas de acceso seleccionadas se quitarán de la lista **Rutas de acceso de confianza**.
