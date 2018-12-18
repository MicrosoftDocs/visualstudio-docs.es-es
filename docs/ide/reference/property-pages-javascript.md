---
title: Página de propiedades, JavaScript
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a35ee6d086153adc718a1616c0c8f0c8c606fbb7
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220035"
---
# <a name="property-pages-javascript"></a>Página de propiedades, JavaScript
Las **Páginas de propiedades** proporcionan acceso a la configuración del proyecto. Puede usar las páginas que aparecen en las **páginas Propiedades** para cambiar las propiedades del proyecto.

Para obtener acceso a las propiedades del proyecto, seleccione un nodo de proyecto en el **Explorador de soluciones**. En el menú **Proyecto**, haga clic en **Propiedades**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

Las siguientes páginas y opciones aparecen en las **páginas Propiedades**.

## <a name="configuration-and-platform-page"></a>Página de configuración y plataforma
 Utilice las siguientes opciones para seleccionar la configuración y la plataforma para mostrar o modificar.

 **Configuración**

 Especifica las opciones de configuración para mostrar o modificar. Los valores son **Depurar** (valor predeterminado), **Liberar**, **Todas las configuraciones** o una configuración definida por el usuario. Para obtener más información, vea [Cómo: Establecer configuraciones Debug y Release en Visual Studio](../../debugger/how-to-set-debug-and-release-configurations.md).

 **Plataforma**

 Especifica la configuración de plataforma para mostrar o modificar. Los valores son **Cualquier CPU** (valor predeterminado para aplicaciones [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)]), **x64**, **ARM**, **x86** o una plataforma definida por el usuario. Para obtener más información, vea [Cómo: Establecer configuraciones Debug y Release en Visual Studio](../../debugger/how-to-set-debug-and-release-configurations.md).

## <a name="general-page"></a>Página general
 Utilice las siguientes opciones para establecer las propiedades generales del proyecto.

> [!NOTE]
> Algunas opciones solo están disponibles en aplicaciones para UWP.


 **Ruta de acceso de salida**

 Especifica la ubicación de los archivos de salida para la configuración del proyecto. La ruta de acceso es relativa. Si escribe una ruta de acceso absoluta, se guarda la ruta de acceso absoluta en el proyecto. La ruta de acceso predeterminada es bin\Debug.

 Cuando utiliza las configuraciones de compilación simplificadas, el sistema del proyecto determina si se debe generar una depuración o versión de lanzamiento. Al hacer clic en **Depurar**, **Iniciar depuración** (o presionar F5), la compilación se coloca en la ubicación de depuración sin tener en cuenta la **Ruta de acceso de salida** que especifique. En cambio, el comando **Compilar solución** en el menú **Compilar** la coloca en la ubicación que especifique. Para habilitar configuraciones de compilación avanzadas, en la barra de menús, pulse **Herramientas**, **Opciones**. En el cuadro de diálogo **Opciones**, expanda **Proyectos y soluciones**, seleccione **General** y, después, desactive la casilla **Mostrar configuraciones de compilación avanzadas**. Esta opción permite controlar manualmente todos los valores de configuración y si se crea una versión de depuración o lanzamiento.

 **Idioma predeterminado**

 Especifica el idioma predeterminado del proyecto. La opción de idioma seleccionada en el Panel de control **Reloj, idioma y región** especifica el idioma preferido del usuario. Al especificar un idioma predeterminado para el proyecto, se asegura de que se usan los recursos de idioma predeterminados especificados si el idioma preferido del usuario no coincide con los recursos de idioma proporcionados en la aplicación.

## <a name="debug-page"></a>Página de depuración
 Utilice las siguientes opciones para establecer las propiedades para depurar el comportamiento en el proyecto.

> [!NOTE]
> Algunas opciones solo están disponibles en aplicaciones para UWP.


 **Depurador para iniciar**

 Especifica el host predeterminado para el depurador.

-   Seleccione **Equipo Local** para iniciar la aplicación en el equipo host de Visual Studio. Para obtener más información, vea [Ejecutar aplicaciones en el equipo local](../../debugger/run-windows-store-apps-on-the-local-machine.md).

-   Seleccione **Simulador** para iniciar la aplicación en el simulador. Para obtener más información, vea [Ejecutar aplicaciones en el simulador](../../debugger/run-windows-store-apps-in-the-simulator.md).

-   Seleccione **Equipo remoto** para iniciar la aplicación en un equipo remoto. Para obtener más información, vea [Ejecutar aplicaciones en un equipo remoto](../../debugger/run-windows-store-apps-on-a-remote-machine.md).

**Iniciar aplicación**

Especifica si se debe iniciar la aplicación cuando presiona F5 o hace clic en **Depurar**, **Iniciar depuración**. Seleccione **Sí** para iniciar la aplicación. En caso contrario, seleccione **No**. Si selecciona **No**, aún puede depurar la aplicación si usa un método diferente para iniciarla.

**Tipo de depurador**

Especifica los tipos de código para depurar. Seleccione **Solo scripts** para depurar código de JavaScript. Seleccione **Solo administrado** para depurar código administrado por Common Language Runtime. Seleccione **Solo nativo** para depurar código de C++. Seleccione **Nativo con Script** para depurar C++ y JavaScript. Seleccione **Mixto (administrado y nativo)** para depurar código administrado y código de C++.

**Permitir bucle invertido de la red local**

Especifica si se permite el acceso a la dirección IP de bucle invertido para probar aplicaciones. Seleccione **Sí** para permitir el uso de la dirección de bucle invertido si la aplicación cliente se encuentra en el mismo equipo en el que se está ejecutando la aplicación de servidor. En caso contrario, seleccione **No**. Esta propiedad está disponible solo si la propiedad **Depurador para iniciar** está establecida en **Equipo remoto**.

**Nombre de equipo**

Especifica el nombre del equipo remoto para hospedar al depurador. Esta propiedad está disponible solo si **Depurador para iniciar** está establecido en **Equipo remoto**.

**Requerir autenticación**

Especifica si el equipo remoto requiere autenticación. Esta propiedad está disponible solo si **Depurador para iniciar** está establecido en **Equipo remoto**.
