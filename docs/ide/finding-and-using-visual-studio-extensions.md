---
title: Búsqueda e instalación de extensiones
ms.date: 09/18/2019
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
ms.openlocfilehash: 9f86aa6cf99ae910c9b10bc6e93c408ca2c85265
ms.sourcegitcommit: a2df993dc5e11c5131dbfcba686f0028a589068f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/20/2019
ms.locfileid: "71150103"
---
# <a name="manage-extensions-for-visual-studio"></a>Administración de extensiones para Visual Studio

Las extensiones son paquetes de código que se ejecutan dentro de Visual Studio y que ofrecen características nuevas o mejoradas. Las extensiones pueden ser controles, ejemplos, plantillas, herramientas u otros componentes que agregan funcionalidad a Visual Studio, como [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsls-vs) o [Visual Studio IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode).

Para obtener información sobre la creación de extensiones de Visual Studio, vea [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Para obtener información sobre el uso de extensiones, consulte la página de la extensión en [Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker range="vs-2017"

## <a name="extensions-and-updates-dialog-box"></a>Cuadro de diálogo Extensiones y actualizaciones

Use el cuadro de diálogo **Extensiones y actualizaciones** para instalar y administrar extensiones de Visual Studio. Para abrir el cuadro de diálogo **Extensiones y actualizaciones**, elija **Herramientas** > **Extensiones y actualizaciones**, o bien escriba **Extensiones** en el cuadro de búsqueda **Inicio rápido**.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="manage-extensions-dialog-box"></a>Cuadro de diálogo Administrar extensiones

Use el cuadro de diálogo **Administrar extensiones** para instalar y administrar extensiones de Visual Studio. Para abrir el cuadro de diálogo **Administrar extensiones**, elija **Extensiones** > **Administrar extensiones**. O bien escriba **Extensiones** en el cuadro de búsqueda y elija **Administrar extensiones**.

::: moniker-end

![Ventana Extensiones de Visual Studio](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

En el panel de la izquierda se clasifican las extensiones en función de las que están instaladas, las que están disponibles en Visual Studio Marketplace (**Online**) y las que tienen actualizaciones disponibles. **Roaming Extension Manager** mantiene una lista de todas las extensiones de Visual Studio que se han instalado en cualquier equipo o instancia de Visual Studio. Se ha diseñado para que pueda buscar las extensiones favoritas más fácilmente.

## <a name="find-and-install-extensions"></a>Búsqueda e instalación de extensiones

::: moniker range="vs-2017"

Puede instalar extensiones desde [Visual Studio Marketplace](https://marketplace.visualstudio.com) o desde el cuadro de diálogo Extensiones y actualizaciones de Visual Studio.

Para instalar extensiones desde Visual Studio:

1. En **Herramientas** > **Extensiones y actualizaciones**, busque la extensión que quiere instalar. Si conoce el nombre o parte del nombre de la extensión, puede buscar en la ventana **Búsqueda**.

2. Seleccione **Descargar**.

   Se programa la instalación de la extensión. Una vez que se hayan cerrado todas las instancias de Visual Studio, se instalará la extensión.

Si intenta instalar una extensión que tiene dependencias, el instalador comprueba si están instaladas. Si no están instaladas, el cuadro de diálogo **Extensiones y actualizaciones** muestra las dependencias que se deben instalar antes de poder instalar la extensión.

### <a name="install-without-using-the-extensions-and-updates-dialog-box"></a>Instalar sin usar el cuadro de diálogo Extensiones y actualizaciones

Es posible que las extensiones empaquetadas en archivos *.vsix* estén disponibles en otras ubicaciones que no sean Visual Studio Marketplace. El cuadro de diálogo **Herramientas** > **Extensiones y actualizaciones** no puede detectar estos archivos, pero se puede instalar un archivo *.vsix* si se hace doble clic en él o si se selecciona y se presiona **ENTRAR**. Después de eso, solo tiene que seguir las instrucciones. Una vez instalada la extensión, puede utilizar el cuadro de diálogo **Extensiones y actualizaciones** para habilitarla, deshabilitarla o desinstalarla.

> [!NOTE]
> - Visual Studio Marketplace contiene las extensiones VSIX y MSI. El cuadro de diálogo Extensiones y actualizaciones no puede habilitar ni deshabilitar las extensiones basadas en MSI.
> - Si una extensión basada en MSI incluye un archivo *extensión.manifiesto_vsix*, la extensión aparece en el cuadro de diálogo **Extensiones y actualizaciones**.

::: moniker-end

::: moniker range=">=vs-2019"

Puede instalar extensiones desde [Visual Studio Marketplace](https://marketplace.visualstudio.com) o desde el cuadro de diálogo Administrar extensiones de Visual Studio.

Para instalar extensiones desde Visual Studio:

1. En **Extensiones** > **Administrar extensiones**, busque la extensión que quiere instalar. (Si conoce el nombre o parte del nombre de la extensión, puede buscar en la ventana **Búsqueda**).

2. Seleccione **Descargar**.

   Se programa la instalación de la extensión. Una vez que se hayan cerrado todas las instancias de Visual Studio, se instalará la extensión.

Si intenta instalar una extensión que tiene dependencias, el instalador comprueba si están instaladas. Si no están instaladas, el cuadro de diálogo **Administrar extensiones** muestra las dependencias que se deben instalar antes de poder instalar la extensión.

### <a name="install-without-using-the-manage-extensions-dialog-box"></a>Instalar sin usar el cuadro de diálogo Administrar extensiones

Es posible que las extensiones empaquetadas en archivos *.vsix* estén disponibles en otras ubicaciones que no sean Visual Studio Marketplace. El cuadro de diálogo **Extensiones** > **Administrar extensiones** no puede detectar estos archivos, pero se puede instalar un archivo *.vsix* si se hace doble clic en él o si se selecciona y se presiona **ENTRAR**. Después de eso, solo tiene que seguir las instrucciones. Una vez instalada la extensión, puede usar el cuadro de diálogo **Administrar extensiones** para habilitarla, deshabilitarla o desinstalarla.

> [!NOTE]
> - Visual Studio Marketplace contiene las extensiones VSIX y MSI. El cuadro de diálogo Administrar extensiones no puede habilitar ni deshabilitar las extensiones basadas en MSI.
> - Si una extensión basada en MSI incluye un archivo *extensión.manifiesto_vsix*, la extensión aparece en el cuadro de diálogo **Administrar extensiones**.

::: moniker-end

## <a name="uninstall-or-disable-an-extension"></a>Desinstalación o deshabilitación de una extensión

Si desea dejar de usar una extensión, puede deshabilitarla o desinstalarla. Al deshabilitar una extensión esta sigue instalada pero está descargada. Busque la extensión y haga clic **Desinstalar** o **Deshabilitar**. Reinicie Visual Studio para descargar una extensión deshabilitada.

> [!NOTE]
> Puede deshabilitar las extensiones VSIX, pero no las extensiones que se instalaron mediante MSI. Las extensiones instaladas mediante MSI solo se pueden desinstalar.

## <a name="per-user-and-administrative-extensions"></a>Extensiones por usuario y administrativas

Las mayoría de las extensiones son por usuario y están instaladas en la carpeta *%LocalAppData%\Microsoft\VisualStudio\\<versión de Visual Studio\>\Extensions\\* . Algunas extensiones son extensiones administrativas y están instaladas en la carpeta *\<<carpeta de instalación de Visual Studio>\Common7\IDE\Extensions\\* .

Para proteger el sistema frente a extensiones que pueden contener errores o código malintencionado, puede limitar que las extensiones por usuario solo se carguen cuando Visual Studio se ejecuta con permisos de usuario normales. Esto significa que las extensiones por usuario están deshabilitadas cuando Visual Studio se ejecuta con permisos elevados.

Para restringir cuándo se cargan las extensiones por usuario:

1. Abra la página de opciones de las extensiones (**Herramientas** > **Opciones** > **Entorno** > **Extensiones**).

2. Desactive la casilla **Cargar extensiones por usuario al ejecutar como administrador**.

3. Reinicie Visual Studio.

## <a name="automatic-extension-updates"></a>Actualizaciones automáticas de extensión

Las extensiones se actualizan de forma automática cuando hay una versión nueva disponible en Visual Studio Marketplace. La versión nueva de la extensión se detecta e instala en segundo plano. La próxima vez que abra Visual Studio, se ejecutará la versión nueva de la extensión.

Si quiere deshabilitar las actualizaciones automáticas, puede deshabilitar la característica para todas las extensiones o solo para extensiones específicas.

::: moniker range="vs-2017"

- Para deshabilitar las actualizaciones automáticas para todas las extensiones, haga clic en el vínculo **Cambiar la configuración de extensiones y actualizaciones** del cuadro de diálogo **Herramientas** > **Extensiones y actualizaciones**. En el cuadro de diálogo **Opciones**, desactive **Actualizar las extensiones automáticamente**.

- Para deshabilitar las actualizaciones automáticas de una extensión específica, desactive la opción **Actualizar esta extensión automáticamente** en el panel de detalles de la extensión situado en el lado derecho del cuadro de diálogo **Extensiones y actualizaciones**.

::: moniker-end

::: moniker range=">=vs-2019"

- Para deshabilitar las actualizaciones automáticas para todas las extensiones, haga clic en el vínculo **Cambiar la configuración para las extensiones** del cuadro de diálogo **Extensiones** > **Administrar extensiones**. En el cuadro de diálogo **Opciones**, desactive **Actualizar las extensiones automáticamente**.

- Para deshabilitar las actualizaciones automáticas de una extensión específica, desactive la opción **Actualizar automáticamente esta extensión** en el panel de detalles de la extensión situado en el lado derecho del cuadro de diálogo **Administrar extensiones**.

::: moniker-end

## <a name="crash-and-unresponsiveness-notifications"></a>Notificaciones de bloqueo y falta de respuesta

Visual Studio avisa si sospecha que una extensión ha estado implicada en un bloqueo durante una sesión anterior. Cuando Visual Studio se bloquea, almacena la pila de excepciones. La próxima vez que Visual Studio se inicia, examina la pila, comenzando por la hoja y dirigiéndose a la base. Si Visual Studio determina que un marco pertenece a un módulo que forma parte de una extensión habilitada e instalada, muestra una notificación.

Visual Studio también avisa si sospecha que una extensión está provocando la falta de respuesta de la interfaz de usuario.

Cuando aparezcan estas notificaciones, puede ignorarlas o realizar una de las acciones siguientes:

::: moniker range="vs-2017"

- Pulse **Deshabilitar esta extensión**. Visual Studio deshabilita la extensión y le permite conocer si necesita reiniciar su sistema para que la deshabilitación surta efecto. Si quiere, puede volver a habilitar la extensión en el cuadro de diálogo **Herramientas** > **Extensiones y actualizaciones**.

::: moniker-end

::: moniker range=">=vs-2019"

- Pulse **Deshabilitar esta extensión**. Visual Studio deshabilita la extensión y le permite conocer si necesita reiniciar su sistema para que la deshabilitación surta efecto. Si quiere, puede volver a habilitar la extensión en el cuadro de diálogo **Extensiones** > **Administrar extensiones**.

::: moniker-end

- Elija **No volver a mostrar este mensaje**.

  - Si la notificación se refiere a un bloqueo en una sesión anterior, Visual Studio ya no muestra una notificación cuando se produzca un bloqueo asociado a esta extensión. Visual Studio seguirá mostrando notificaciones cuando la falta de respuesta pueda estar asociada con esta extensión, o para los bloqueos o faltas de respuesta que puedan estar asociados a otras extensiones.
  - Si la notificación se refiere a una falta de respuesta, en el IDE (entorno de desarrollo integrado) ya no se muestra una notificación cuando esa extensión esté asociada a la falta de respuesta. Visual Studio seguirá mostrando notificaciones relacionadas con los bloqueos para esta extensión, así como notificaciones relacionadas con bloqueos y faltas de respuesta para otras extensiones.

- Seleccione **Más información** para navegar a esta página.

- Pulse el botón **X** al final de la notificación para descartarla. Aparecerá una nueva notificación para las instancias futuras de la extensión que estén asociadas con un bloqueo o falta de respuesta de la interfaz de usuario.

> [!NOTE]
> Una notificación de bloqueo o falta de respuesta de la interfaz de usuario significa únicamente que uno de los módulos de la extensión estaba en la pila cuando la interfaz de usuario dejó de responder o cuando se produjo el bloqueo. No necesariamente significa que la propia extensión sea la causa. Es posible que la extensión llamara a código que forma parte de Visual Studio, lo que a su vez dio lugar a una falta de respuesta de la interfaz de usuario o a un bloqueo. Sin embargo, la notificación puede seguir siendo útil si el escenario que ha provocado la falta de respuesta de la interfaz de usuario el bloqueo no es importante para usted. En este caso, deshabilitar la extensión evita el mismo bloqueo o falta de respuesta de la interfaz de usuario en el futuro sin afectar a su productividad.

## <a name="samples"></a>Muestras

Cuando se instala un ejemplo en línea, la solución se almacena en dos ubicaciones:

- Se almacena una copia de trabajo en la ubicación especificada al crear el proyecto.

- Se almacena una copia maestra independiente en el equipo.

::: moniker range="vs-2017"

Puede usar el cuadro de diálogo **Herramientas** > **Extensiones y actualizaciones** para realizar estas tareas relacionadas con ejemplos:

::: moniker-end

::: moniker range=">=vs-2019"

Puede usar el cuadro de diálogo **Extensiones** > **Administrar extensiones** para realizar estas tareas relacionadas con ejemplos:

::: moniker-end

- Enumerar las copias maestras de ejemplos que ha instalado.

- Deshabilitar o desinstalar la copia maestra de un ejemplo.

- Instalar paquetes de ejemplo, que son colecciones de ejemplos relacionados con una tecnología o una característica.

- Instalar ejemplos en línea individuales.

- Ver notificaciones de actualización cuando se publiquen cambios en el código fuente de los ejemplos instalados.

- Actualizar la copia maestra de un ejemplo instalado cuando haya una notificación de actualización.

## <a name="see-also"></a>Vea también

- [Visual Studio Marketplace](https://marketplace.visualstudio.com)
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)