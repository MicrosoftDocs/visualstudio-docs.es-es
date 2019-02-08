---
title: Búsqueda y uso de extensiones
ms.date: 01/30/2019
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 766d2e87361ad191b985272a8e1de8a6fa272353
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484087"
---
# <a name="find-and-use-visual-studio-extensions"></a>Búsqueda y uso de extensiones de Visual Studio

Las extensiones de Visual Studio son paquetes de códigos que se ejecutan dentro de Visual Studio y que ofrecen características nuevas o mejoradas de Visual Studio. Encontrará más información sobre las extensiones de Visual Studio aquí: [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

Use el cuadro de diálogo **Extensiones y actualizaciones** para instalar y administrar extensiones de Visual Studio. Para abrir el cuadro de diálogo **Extensiones y actualizaciones**, seleccione **Herramientas** > **Extensiones y actualizaciones**, o bien escriba **Extensiones** en la ventana **Inicio rápido**.

![Cuadro de diálogo Extensiones y actualizaciones de Visual Studio](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

En el panel de la izquierda se clasifican las extensiones en función de las que están instaladas, las que están disponibles en Visual Studio Marketplace (**Online**) y las que tienen actualizaciones disponibles. **Roaming Extension Manager** mantiene una lista de todas las extensiones de Visual Studio que se han instalado en cualquier equipo o instancia de Visual Studio. Se ha diseñado para que pueda buscar las extensiones favoritas más fácilmente.

## <a name="find-visual-studio-extensions"></a>Búsqueda de extensiones de Visual Studio

Puede instalar las extensiones desde [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Las extensiones pueden ser controles, ejemplos, plantillas, herramientas u otros componentes que agregan funcionalidad a Visual Studio. Visual Studio admite extensiones con el formato de paquete VSIX; esto incluye plantillas de proyecto, plantillas de elementos, elementos del **Cuadro de herramientas** , componentes de Managed Extension Framework (MEF) y VSPackages. También puede descargar e instalar extensiones basadas en MSI, pero el cuadro de diálogo **Extensiones y actualizaciones** no puede habilitarlas ni deshabilitarlas. Visual Studio Marketplace contiene extensiones VSIX y MSI.

## <a name="install-or-uninstall-visual-studio-extensions"></a>Instalación o desinstalación de extensiones de Visual Studio

En **Extensiones y actualizaciones**, busque la extensión que desea instalar. (Si conoce el nombre o parte del nombre de la extensión, puede buscar en la ventana **Búsqueda**). Haga clic en **Descargar**. Se programa la instalación de la extensión. Una vez que se hayan cerrado todas las instancias de Visual Studio, se instalará la extensión.

Si intenta instalar una extensión que tiene dependencias, el instalador comprueba si están instaladas. Si no están instaladas, el cuadro de diálogo **Extensiones y actualizaciones** muestra las dependencias que se deben instalar antes de poder instalar la extensión.

Si desea dejar de usar una extensión, puede deshabilitarla o desinstalarla. Al deshabilitar una extensión esta sigue instalada pero está descargada. Solo puede deshabilitar las extensiones VSIX; las extensiones que se instalaron mediante MSI solo se pueden desinstalar. Busque la extensión y haga clic **Desinstalar** o **Deshabilitar**. Reinicie Visual Studio para descargar una extensión deshabilitada.

## <a name="per-user-and-administrative-extensions"></a>Extensiones por usuario y administrativas

Las mayoría de las extensiones son extensiones por usuario y están instaladas en la carpeta *%LocalAppData%\Microsoft\VisualStudio\\<versión de Visual Studio\>\Extensions\\*. Algunas extensiones son extensiones administrativas y están instaladas en la carpeta *\<<carpeta de instalación de Visual Studio>\Common7\IDE\Extensions\\*.

Para proteger el sistema frente a extensiones que pueden contener errores o código malintencionado, puede limitar que las extensiones por usuario solo se carguen cuando Visual Studio se ejecuta con permisos de usuario normales. Esto significa que las extensiones por usuario están deshabilitadas cuando Visual Studio se ejecuta con permisos de usuario administrativo. Para ello, vaya a la página de opciones **Extensiones y actualizaciones** (**Herramientas > Opciones** > **Entorno** > **Extensiones y actualizaciones**). Desactive la casilla **Cargar extensiones por usuario al ejecutar como administrador** y reinicie Visual Studio.

## <a name="automatic-extension-updates"></a>Actualizaciones automáticas de extensión

Las extensiones se actualizan de forma automática cuando hay una versión nueva disponible en Visual Studio Marketplace. La versión nueva de la extensión se detecta e instala en segundo plano. La próxima vez que inicie Visual Studio, se ejecutará la versión nueva de la extensión.

Si desea deshabilitar las actualizaciones automáticas, puede deshabilitar la característica para todas las extensiones o solo para extensiones específicas.

- Para deshabilitar las actualizaciones automáticas para todas las extensiones, haga clic en el vínculo **Cambiar la configuración de extensiones y actualizaciones** del cuadro de diálogo **Extensiones y actualizaciones**. En el cuadro de diálogo **Opciones**, desactive **Actualizar las extensiones automáticamente**.

- Para deshabilitar las actualizaciones automáticas de una extensión específica, desactive la opción **Actualizar esta extensión automáticamente** en el panel de detalles de la extensión situado en el lado derecho del cuadro de diálogo **Extensiones y actualizaciones**.

## <a name="extension-crash-and-unresponsiveness-notifications"></a>Notificaciones de bloqueo y falta de respuesta de una extensión

Como novedad en **Visual Studio 2017 (versión 15.3)**, Visual Studio le notifica si sospecha que una extensión estaba implicada en un bloqueo durante una sesión anterior. Cuando Visual Studio se bloquea, almacena la pila de excepciones. La próxima vez que Visual Studio se inicia, examina la pila, comenzando por la hoja y dirigiéndose a la base. Si Visual Studio determina que un marco pertenece a un módulo que forma parte de una extensión habilitada e instalada, muestra una notificación.

Como novedad en **Visual Studio 2017, versión 15.6**, Visual Studio también le notifica si sospecha que una extensión está causando la falta de respuesta de la interfaz de usuario.

Cuando aparezcan estas notificaciones, puede ignorarlas o realizar una de las acciones siguientes:

- Pulse **Deshabilitar esta extensión**. Visual Studio deshabilita la extensión y le permite conocer si necesita reiniciar su sistema para que la deshabilitación surta efecto. Puede volver a habilitar la extensión en el cuadro de diálogo **Extensiones y actualizaciones** si quiere.

- Elija **No volver a mostrar este mensaje**.

  - Si la notificación se refiere a un bloqueo en una sesión anterior, Visual Studio ya no muestra una notificación cuando se produzca un bloqueo asociado a esta extensión. Visual Studio seguirá mostrando notificaciones cuando la falta de respuesta pueda estar asociada con esta extensión, o para los bloqueos o faltas de respuesta que puedan estar asociados a otras extensiones.
  - Si la notificación se refiere a una falta de respuesta, en el IDE ya no se muestra una notificación cuando esa extensión esté asociada a la falta de respuesta. Visual Studio seguirá mostrando notificaciones relacionadas con los bloqueos para esta extensión, y notificaciones relacionadas con bloqueos y faltas de respuesta para otras extensiones.

- Elija **Más información** para llegar a esta página.

- Pulse el botón **X** al final de la notificación para descartarla. Aparecerá una nueva notificación para las instancias futuras de la extensión que estén asociadas con un bloqueo o falta de respuesta de la interfaz de usuario.

> [!NOTE]
> Una notificación de bloqueo o falta de respuesta de la interfaz de usuario significa únicamente que uno de los módulos de la extensión estaba en la pila cuando la interfaz de usuario dejó de responder o cuando se produjo el bloqueo. No necesariamente significa que la propia extensión sea la causa. Es posible que la extensión llamara a código que forma parte de Visual Studio, lo que a su vez dio lugar a una falta de respuesta de la interfaz de usuario o a un bloqueo. Sin embargo, la notificación puede seguir siendo útil si el escenario que ha provocado la falta de respuesta de la interfaz de usuario el bloqueo no es importante para usted. En este caso, deshabilitar la extensión evita el mismo bloqueo o falta de respuesta de la interfaz de usuario en el futuro sin afectar a su productividad.

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

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Instalar sin usar el cuadro de diálogo Extensiones y actualizaciones

Es posible que las extensiones empaquetadas en archivos *.vsix* estén disponibles en otras ubicaciones que no sean Visual Studio Marketplace. El cuadro de diálogo **Extensiones y actualizaciones** no puede detectar estos archivos, pero puede instalar un archivo *.vsix* si hace doble clic en él y presiona la tecla **Entrar**. Después de eso, solo tiene que seguir las instrucciones. Una vez instalada la extensión, puede utilizar el cuadro de diálogo **Extensiones y actualizaciones** para habilitarla, deshabilitarla o desinstalarla.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Tipos de extensiones que no admite el cuadro de diálogo Extensiones y actualizaciones

Visual Studio sigue siendo compatible con las extensiones que se instalan con Microsoft Installer (MSI), pero no a través del cuadro de diálogo **Extensiones y actualizaciones** sin ninguna modificación.

> [!TIP]
> Si una extensión basada en MSI incluye un archivo *extensión.manifiesto_vsix*, la extensión aparece en el cuadro de diálogo **Extensiones y actualizaciones**.