---
title: Buscar y usar extensiones de Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 06/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0327ccaa52f3bd348246eea39b754f5c9069f3a1
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="finding-and-using-visual-studio-extensions"></a>Buscar y usar extensiones de Visual Studio
Las extensiones de Visual Studio son paquetes de códigos que se ejecutan dentro de Visual Studio y que ofrecen características nuevas o mejoradas de Visual Studio. Encontrará más información sobre las extensiones de Visual Studio aquí: [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  

 Puede utilizar el cuadro de diálogo **Extensiones y actualizaciones** para instalar extensiones y ejemplos de Visual Studio desde sitios web y otras ubicaciones y, después, habilitarlas, deshabilitarlas, actualizarlas o desinstalarlas. (**Herramientas / Extensiones y actualizaciones**o escriba **Extensiones** en la ventana **Inicio rápido** ). El cuadro de diálogo también muestra las actualizaciones de los ejemplos instalados y extensiones. También puede descargar extensiones de sitios web, o puede obtenerlas de otros desarrolladores.  

> [!NOTE]
>  A partir de Visual Studio 2015, las extensiones hospedadas en Visual Studio Marketplace se actualizarán automáticamente.  Puede cambiar esta configuración en el cuadro de diálogo **Extensiones y actualizaciones** .  Vea la sección sobre **Actualizaciones automáticas de extensión** a continuación para obtener más información.  

## <a name="finding-visual-studio-extensions"></a>Buscar extensiones de Visual Studio  
 Puede instalar extensiones desde [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Las extensiones pueden ser controles, ejemplos, plantillas, herramientas u otros componentes que agregan funcionalidad a Visual Studio. Visual Studio admite extensiones con el formato de paquete VSIX; esto incluye plantillas de proyecto, plantillas de elementos, elementos del **Cuadro de herramientas** , componentes de Managed Extension Framework (MEF) y VSPackages. También puede descargar e instalar extensiones basadas en MSI, pero el cuadro de diálogo **Extensiones y actualizaciones** no puede habilitarlas ni deshabilitarlas. Visual Studio Marketplace contiene extensiones VSIX y MSI.  

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Instalar o desinstalar extensiones de Visual Studio  
 En **Extensiones y actualizaciones**, busque la extensión que desea instalar. (Si conoce el nombre o parte del nombre de la extensión, puede buscar en la ventana **Búsqueda**). Haga clic en **Descargar**.  Se programará la instalación de la extensión. Una vez que se hayan cerrado todas las instancias de Visual Studio, se instalará la extensión.

 Si intenta instalar una extensión que tiene dependencias, el instalador comprueba si están instaladas. Si no están instaladas, el cuadro de diálogo **Extensiones y actualizaciones** muestra las dependencias que se deben instalar antes de poder instalar la extensión.  

 Si desea dejar de usar una extensión, puede deshabilitarla o desinstalarla. Al deshabilitar una extensión esta sigue instalada pero está descargada. Solo puede deshabilitar las extensiones VSIX; las extensiones que se instalaron mediante MSI solo se pueden desinstalar. Busque la extensión y haga clic **Desinstalar** o **Deshabilitar**. Para descargar una extensión deshabilitada, debe reiniciar Visual Studio.  

## <a name="per-user-and-administrative-extensions"></a>Extensiones por usuario y administrativas  
 Las mayoría de las extensiones son extensiones por usuario y están instaladas en la carpeta **%LocalAppData%\Microsoft\VisualStudio\\<versión de Visual Studio\>\Extensions\\**. Algunas extensiones son extensiones administrativas y están instaladas en la carpeta **\<<carpeta de instalación de Visual Studio>\Common7\IDE\Extensions\\**.  

 Para proteger el sistema frente a extensiones que pueden contener errores o código malintencionado, puede limitar que las extensiones por usuario solo se carguen cuando Visual Studio se ejecuta con permisos de usuario normales. Esto significa que las extensiones por usuario están deshabilitadas cuando Visual Studio se ejecuta con permisos de usuario administrativo. Para ello, vaya a la página de opciones **Extensiones y actualizaciones** (**Herramientas / Opciones**, **Entorno**, **Extensiones y actualizaciones**, o simplemente escriba **Extensión** en la ventana **Inicio rápido** ). Desactive la casilla **Cargar extensiones por usuario al ejecutar como administrador** y reinicie Visual Studio.  

## <a name="automatic-extension-updates"></a>Actualizaciones automáticas de extensión  
 Las extensiones por usuario se actualizan automáticamente cuando hay disponible una versión nueva para Visual Studio Marketplace.  La nueva versión de la extensión se detecta y se instala en segundo plano y se ejecutará en el próximo reinicio de Visual Studio.  

 Únicamente las extensiones por usuario se pueden actualizar automáticamente.  Las extensiones administrativas instaladas para todos los usuarios no se actualizarán y deberá seguir instalando las versiones nuevas mediante el nodo **Actualizaciones** del cuadro de diálogo **Extensiones y actualizaciones**. Puede ver las extensiones que se actualizarán automáticamente en el panel de detalles de la extensión del cuadro de diálogo **Extensiones y actualizaciones**.  

 Si desea deshabilitar las actualizaciones automáticas, puede deshabilitar la característica para todas las extensiones o solo para extensiones específicas.  

-   Para deshabilitar las actualizaciones automáticas para todas las extensiones, pulse el vínculo **Cambiar la configuración de extensiones y actualizaciones** en el cuadro de diálogo **Extensiones y actualizaciones** y desactive la opción **Actualizar las extensiones automáticamente**.  

-   Para deshabilitar las actualizaciones automáticas de una extensión específica, desactive la opción **Actualizar esta extensión automáticamente** en el panel de detalles de la extensión situado en el lado derecho del cuadro de diálogo **Extensiones y actualizaciones**.  

> [!NOTE]
>  A partir de Visual Studio 2015 Update 2, puede especificar (en **Herramientas / Opciones / Entorno / Extensiones y actualizaciones**) si quiere actualizaciones automáticas para las extensiones por usuario, todas las extensiones de usuario o ambas (la configuración predeterminada).  

## <a name="extension-crash-notifications"></a>Notificaciones de bloqueo de extensiones

En Visual Studio 2017 (versión 15.3: versión preliminar), Visual Studio le notifica si sospecha que una extensión estaba implicada en un bloqueo durante una sesión anterior. Cuando Visual Studio se bloquea, almacena la pila de excepciones. La próxima vez que Visual Studio se inicia, examina la pila, comenzando por la hoja y dirigiéndose a la base. Si Visual Studio determina que un marco pertenece a un módulo que forma parte de una extensión habilitada e instalada, le notifica con un mensaje como:

  "Una sesión anterior ha finalizado de manera inesperada. Deshabilitar la extensión "nombre_extensión" puede ayudar a evitar problemas similares".

Puede ignorar la notificación o realizar una de las acciones siguientes:

-   Pulse **Deshabilitar esta extensión**. Visual Studio deshabilita la extensión y le permite conocer si necesita reiniciar su sistema para que la deshabilitación surta efecto. Puede volver a habilitar la extensión en el cuadro de diálogo **Extensiones y actualizaciones** si quiere.

-   Pulse **No mostrar de nuevo para esta extensión**. El IDE ya no mostrará notificaciones de los bloqueos asociados con esta extensión, pero mostrará notificaciones de los bloqueos asociados con otras extensiones.

-   Pulse **Más información** para ver este tema de ayuda en su explorador predeterminado.

-   Pulse el botón **X** al final de la notificación para descartarla. Si la misma extensión está implicada en un bloqueo en una sesión futura, la notificación aparecerá de nuevo.

> [!NOTE]
>  Una notificación de bloqueo significa solo que uno de los módulos de la extensión estaba en la pila del bloqueo. No necesariamente significa que la propia extensión ha provocado el bloqueo. Es posible que la extensión llamara a código que forma parte de Visual Studio y que ese código provocara el bloqueo. En cambio, la notificación puede seguir siendo útil si el escenario que ha provocado el bloqueo no es importante para usted. En este caso, deshabilitar la extensión evita el mismo bloqueo en el futuro sin afectar a su productividad.


## <a name="sample-master-copies-and-working-copies"></a>Copias maestras y copias de trabajo de muestra  
 Cuando se instala un ejemplo en línea, la solución se almacena en dos ubicaciones:  

-   Se almacena una copia de trabajo en la ubicación especificada en el cuadro de diálogo **Nuevo proyecto** .  

-   Se almacena una copia maestra independiente en el equipo.  

 Puede utilizar el cuadro de diálogo **Extensiones y actualizaciones** para realizar estas tareas relacionadas con ejemplos:  

-   Enumerar las copias maestras de ejemplos que ha instalado.  

-   Deshabilitar o desinstalar la copia maestra de un ejemplo.  

-   Instalar paquetes de ejemplo, que son colecciones de ejemplos relacionados con una tecnología o una característica.  

-   Instalar ejemplos en línea individuales. (También puede hacerlo en el cuadro de diálogo **Nuevo proyecto** ).  

-   Ver notificaciones de actualización cuando se publiquen cambios en el código fuente de los ejemplos instalados.  

-   Actualizar la copia maestra de un ejemplo instalado cuando haya una notificación de actualización.  

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Instalar sin utilizar el cuadro de diálogo Extensiones y actualizaciones  
 Las extensiones empaquetadas en archivos .vsix pueden estar disponibles en ubicaciones distintas de Visual Studio Marketplace. El cuadro de diálogo **Extensiones y actualizaciones** no puede detectar estos archivos, pero puede instalar un archivo .vsix si hace doble clic en el archivo y presiona la tecla ENTRAR. Después de eso, solo tiene que seguir las instrucciones. Una vez instalada la extensión, puede utilizar el cuadro de diálogo **Extensiones y actualizaciones** para habilitarla, deshabilitarla o desinstalarla.  

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Tipos de extensiones que no admite el cuadro de diálogo Extensiones y actualizaciones  
 Visual Studio sigue siendo compatible con las extensiones que se instalan con Microsoft Installer (MSI), pero no a través del cuadro de diálogo **Extensiones y actualizaciones** sin ninguna modificación.  

> [!TIP]
>  Si una extensión basada en MSI incluye un archivo extension.vsixmanifest, la extensión aparecerá en el cuadro de diálogo **Extensiones y actualizaciones** .
