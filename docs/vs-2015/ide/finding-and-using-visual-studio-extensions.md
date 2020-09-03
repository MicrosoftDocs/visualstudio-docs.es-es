---
title: Buscar y usar extensiones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: df6219a66b0f6c85e197b209741706abc7ce3d06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655874"
---
# <a name="finding-and-using-visual-studio-extensions"></a>Buscar y usar extensiones de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las extensiones de Visual Studio son paquetes de códigos que se ejecutan dentro de Visual Studio y que ofrecen características nuevas o mejoradas de Visual Studio. Encontrará más información sobre las extensiones de Visual Studio aquí: [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Puede utilizar el cuadro de diálogo **Extensiones y actualizaciones** para instalar extensiones y ejemplos de Visual Studio desde sitios web y otras ubicaciones y, después, habilitarlas, deshabilitarlas, actualizarlas o desinstalarlas. (**Herramientas / Extensiones y actualizaciones**o escriba **Extensiones** en la ventana **Inicio rápido** ). El cuadro de diálogo también muestra las actualizaciones de los ejemplos instalados y extensiones. También puede descargar extensiones de sitios web, o puede obtenerlas de otros desarrolladores.

> [!NOTE]
> A partir de Visual Studio 2015, las extensiones de la Galería de Visual Studio se actualizarán automáticamente.  Puede cambiar esta configuración en el cuadro de diálogo **Extensiones y actualizaciones** .  Vea la sección sobre **Actualizaciones automáticas de extensión** a continuación para obtener más información.

## <a name="finding-visual-studio-extensions"></a>Buscar extensiones de Visual Studio
 Puede instalar las extensiones de la [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o de la [Galería de ejemplos](https://code.msdn.microsoft.com/vstudio) en el sitio web de Microsoft. Las extensiones pueden ser controles, ejemplos, plantillas, herramientas u otros componentes que agregan funcionalidad a Visual Studio. Visual Studio admite extensiones con el formato de paquete VSIX; esto incluye plantillas de proyecto, plantillas de elementos, elementos del **Cuadro de herramientas** , componentes de Managed Extension Framework (MEF) y VSPackages. También puede descargar e instalar extensiones basadas en MSI, pero el cuadro de diálogo **Extensiones y actualizaciones** no puede habilitarlas ni deshabilitarlas. La Galería de Visual Studio contiene extensiones VSIX y MSI.

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Instalar o desinstalar extensiones de Visual Studio
 En **Extensiones y actualizaciones**, busque la extensión que desea instalar. (Si conoce el nombre o parte del nombre de la extensión, puede buscar en la ventana Buscar en la **Galería de Visual Studio** ). Haga clic en **Descargar**y, a continuación, en **instalar**. Para cargar la extensión, debe reiniciar Visual Studio.

 Si intenta instalar una extensión que tiene dependencias, el instalador comprueba si están instaladas. Si no están instaladas, el cuadro de diálogo **Extensiones y actualizaciones** muestra las dependencias que se deben instalar antes de poder instalar la extensión.

 Si desea dejar de usar una extensión, puede deshabilitarla o desinstalarla. Al deshabilitar una extensión esta sigue instalada pero está descargada. Solo puede deshabilitar las extensiones VSIX; las extensiones que se instalaron mediante MSI solo se pueden desinstalar. Busque la extensión y haga clic **Desinstalar** o **Deshabilitar**. Para descargar una extensión deshabilitada, debe reiniciar Visual Studio.

## <a name="per-user-and-administrative-extensions"></a>Extensiones por usuario y administrativas
 Las mayoría de las extensiones son extensiones por usuario y están instaladas en la carpeta **%LocalAppData%\Microsoft\VisualStudio\\<versión de Visual Studio\>\Extensions\\**. Algunas extensiones son extensiones administrativas y se instalan en la carpeta ** \<Visual Studio installation folder> \Common7\IDE\Extensions \\ **

 Para proteger el sistema frente a extensiones que pueden contener errores o código malintencionado, puede limitar que las extensiones por usuario solo se carguen cuando Visual Studio se ejecuta con permisos de usuario normales. Esto significa que las extensiones por usuario están deshabilitadas cuando Visual Studio se ejecuta con permisos de usuario administrativo. Para ello, vaya a la página de opciones **Extensiones y actualizaciones** (**Herramientas / Opciones**, **Entorno**, **Extensiones y actualizaciones**, o simplemente escriba **Extensión** en la ventana **Inicio rápido** ). Desactive la casilla **Cargar extensiones por usuario al ejecutar como administrador** y reinicie Visual Studio.

## <a name="automatic-extension-updates"></a>Actualizaciones automáticas de extensión
 Las extensiones por usuario se actualizan automáticamente cuando hay disponible una versión nueva en la Galería de Visual Studio.  La nueva versión de la extensión se detecta y se instala en segundo plano y se ejecutará en el próximo reinicio de Visual Studio.

 Únicamente las extensiones por usuario se pueden actualizar automáticamente.  Las extensiones administrativas instaladas para todos los usuarios no se actualizarán y deberá seguir instalando las versiones nuevas mediante el nodo **Actualizaciones** del cuadro de diálogo **Extensiones y actualizaciones** . Puede ver las extensiones que se actualizarán automáticamente en el panel de detalles de la extensión del cuadro de diálogo **extensiones y actualizaciones** .

 Si desea deshabilitar las actualizaciones automáticas, puede deshabilitar la característica para todas las extensiones o solo para extensiones específicas.

- Para deshabilitar las actualizaciones automáticas para todas las extensiones, haga clic en el vínculo **Cambiar la configuración de extensiones y actualizaciones** en el cuadro de diálogo **Extensiones y actualizaciones** y desactive la opción **Actualizar las extensiones automáticamente**.

- Para deshabilitar las actualizaciones automáticas de una extensión específica, desactive la opción **Actualizar esta extensión automáticamente** en el panel de detalles de la extensión, en el lado derecho del cuadro de diálogo **extensiones y actualizaciones** .

> [!NOTE]
> A partir de Visual Studio 2015 Update 2, puede especificar (en **Herramientas / Opciones / Entorno / Extensiones y actualizaciones**) si quiere actualizaciones automáticas para las extensiones por usuario, todas las extensiones de usuario o ambas (la configuración predeterminada).

## <a name="sample-master-copies-and-working-copies"></a>Copias maestras y copias de trabajo de muestra
 Cuando se instala un ejemplo en línea, la solución se almacena en dos ubicaciones:

- Se almacena una copia de trabajo en la ubicación especificada en el cuadro de diálogo **Nuevo proyecto** .

- Se almacena una copia maestra independiente en el equipo.

  Puede utilizar el cuadro de diálogo **Extensiones y actualizaciones** para realizar estas tareas relacionadas con ejemplos:

- Enumerar las copias maestras de ejemplos que ha instalado.

- Deshabilitar o desinstalar la copia maestra de un ejemplo.

- Instalar paquetes de ejemplo, que son colecciones de ejemplos relacionados con una tecnología o una característica.

- Instalar ejemplos en línea individuales. (También puede hacerlo en el cuadro de diálogo **Nuevo proyecto** ).

- Ver notificaciones de actualización cuando se publiquen cambios en el código fuente de los ejemplos instalados.

- Actualizar la copia maestra de un ejemplo instalado cuando haya una notificación de actualización.

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Instalar sin utilizar el cuadro de diálogo Extensiones y actualizaciones
 Las extensiones empaquetadas en archivos .vsix pueden estar disponibles en ubicaciones distintas de la Galería de Visual Studio. El cuadro de diálogo **Extensiones y actualizaciones** no puede detectar estos archivos, pero puede instalar un archivo .vsix si hace doble clic en el archivo y presiona la tecla ENTRAR. Después de eso, solo tiene que seguir las instrucciones. Una vez instalada la extensión, puede utilizar el cuadro de diálogo **Extensiones y actualizaciones** para habilitarla, deshabilitarla o desinstalarla.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Tipos de extensiones que no admite el cuadro de diálogo Extensiones y actualizaciones
 Visual Studio sigue siendo compatible con las extensiones que se instalan con Microsoft Installer (MSI), pero no a través del cuadro de diálogo **Extensiones y actualizaciones** sin ninguna modificación.

> [!TIP]
> Si una extensión basada en MSI incluye un archivo extension.vsixmanifest, la extensión aparecerá en el cuadro de diálogo **Extensiones y actualizaciones** .
