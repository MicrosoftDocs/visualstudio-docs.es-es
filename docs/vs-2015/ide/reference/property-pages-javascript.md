---
title: Página de propiedades, JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffb1298981481bde063de898dc81c02dad548888
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297826"
---
# <a name="property-pages-javascript"></a>Página de propiedades, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Las **páginas Propiedades** proporcionan acceso a la configuración del proyecto. Puede usar las páginas que aparecen en las **páginas Propiedades** para cambiar las propiedades del proyecto.

 Para obtener acceso a las propiedades del proyecto, seleccione un nodo de proyecto en el **Explorador de soluciones**. En el menú **Proyecto**, haga clic en **Propiedades**.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 Las siguientes páginas y opciones aparecen en las **páginas Propiedades**.

## <a name="configuration-and-platform-page"></a>Página de configuración y plataforma
 Utilice las siguientes opciones para seleccionar la configuración y la plataforma para mostrar o modificar.

 **Configuration** Specifies the configuration settings to display or modify. Los valores son **Depurar** (valor predeterminado), **Liberar**, **Todas las configuraciones** o una configuración definida por el usuario. Para obtener más información, consulte [Configuraciones Debug y Release](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Platform** Specifies the platform settings to display or modify. Los valores son **Cualquier CPU** (valor predeterminado para aplicaciones [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)]), **x64**, **ARM**, **x86** o una plataforma definida por el usuario. Para obtener más información, consulte [Configuraciones Debug y Release](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="general-page"></a>Página general
 Utilice las siguientes opciones para establecer las propiedades generales del proyecto.

> [!NOTE]
> Algunas opciones solo están disponibles en aplicaciones de la Tienda Windows.

 **Output Path** Specifies the location of the output files for the project's configuration. La ruta de acceso es relativa. Si escribe una ruta de acceso absoluta, se guarda la ruta de acceso absoluta en el proyecto. La ruta de acceso predeterminada es bin\Debug.

 Cuando utiliza las configuraciones de compilación simplificadas, el sistema del proyecto determina si se debe generar una depuración o versión de lanzamiento. Al hacer clic en **Depurar**, **Iniciar depuración** (o presionar F5), la compilación se coloca en la ubicación de depuración sin tener en cuenta la **Ruta de acceso de salida** que especifique. En cambio, el comando **Compilar solución** en el menú **Compilar** la coloca en la ubicación que especifique. Para habilitar configuraciones de compilación avanzadas, en la barra de menús, pulse **Herramientas**, **Opciones**. En el cuadro de diálogo **Opciones**, expanda **Proyectos y soluciones**, seleccione **General** y, después, desactive la casilla **Mostrar configuraciones de compilación avanzadas**. Esta opción permite controlar manualmente todos los valores de configuración y si se crea una versión de depuración o lanzamiento. For more information, see [NIB: General, Projects and Solutions, Options Dialog Box](https://msdn.microsoft.com/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).

 **Default Language** Specifies the default language for the project. La opción de idioma seleccionada en el Panel de control **Reloj, idioma y región** especifica el idioma preferido del usuario. Al especificar un idioma predeterminado para el proyecto, se asegura de que se utilizan los recursos de idioma predeterminados especificados si el idioma preferido del usuario no coincide con los recursos de idioma proporcionados en la aplicación.

## <a name="debug-page"></a>Página de depuración
 Utilice las siguientes opciones para establecer las propiedades para depurar el comportamiento en el proyecto.

> [!NOTE]
> Algunas opciones solo están disponibles en aplicaciones de la Tienda Windows.

 **Debugger to Launch** Specifies the default host for the debugger.

- Seleccione **Equipo Local** para iniciar la aplicación en el equipo host de Visual Studio. Para obtener más información, vea [Ejecutar aplicaciones en el equipo local](https://go.microsoft.com/fwlink/?LinkId=234912).

- Seleccione **Simulador** para iniciar la aplicación en el simulador. Para obtener más información, vea [Ejecutar aplicaciones en el simulador](https://go.microsoft.com/fwlink/?LinkId=234913).

- Seleccione **Equipo remoto** para iniciar la aplicación en un equipo remoto. Para obtener más información, vea [Ejecutar aplicaciones en un equipo remoto](https://go.microsoft.com/fwlink/?LinkId=234914).

  **Launch Application** Specifies whether to start the application when you press F5 or click **Debug**, **Start Debugging**. Seleccione **Sí** para iniciar la aplicación. En caso contrario, seleccione **No**. Si selecciona **No**, aún puede depurar la aplicación si usa un método diferente para iniciarla.

  **Debugger Type** Specifies the types of code to debug. Seleccione **Solo scripts** para depurar código de JavaScript. Seleccione **Solo administrado** para depurar código administrado por Common Language Runtime. Seleccione **Solo nativo** para depurar código de C++. Seleccione **Nativo con Script** para depurar C++ y JavaScript. Seleccione **Mixto (administrado y nativo)** para depurar código administrado y código de C++.

  **Allow Local Network Loopback** Specifies whether access to the IP loopback address is allowed for app testing. Seleccione **Sí** para permitir el uso de la dirección de bucle invertido si la aplicación cliente se encuentra en el mismo equipo en el que se está ejecutando la aplicación de servidor. En caso contrario, seleccione **No**. Esta propiedad está disponible solo si la propiedad **Depurador para iniciar** está establecida en **Equipo remoto**.

  **Machine Name** Specifies the name of the remote computer to host the debugger. Esta propiedad está disponible solo si **Depurador para iniciar** está establecido en **Equipo remoto**.

  **Require Authentication** Specifies whether the remote computer requires authentication. Esta propiedad está disponible solo si **Depurador para iniciar** está establecido en **Equipo remoto**.
