---
title: "P&#225;gina de propiedades, JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "javascript.project.property.debugging.debuggertype"
  - "javascript.project.property.debugging.requireauthentication"
  - "javascript.project.property.outputpath"
  - "javascript.project.property.debugging.launchapplication"
  - "javascript.project.property.defaultlanguage"
  - "javascript.project.property.debugging.machinename"
  - "javascript.project.property.debugging.allowlocalnetworkloopback"
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# P&#225;gina de propiedades, JavaScript
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Las **páginas Propiedades** proporcionan acceso a la configuración del proyecto.  Puede utilizar las páginas que aparecen en las **páginas Propiedades** para cambiar las propiedades del proyecto.  
  
 Para obtener acceso a las propiedades del proyecto, seleccione un nodo de proyecto en el **Explorador de soluciones**.  En el menú **Proyecto**, haga clic en **Propiedades**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
 Las siguientes páginas y opciones aparecen en las **páginas Propiedades**.  
  
## Página de configuración y plataforma  
 Utilice las siguientes opciones para seleccionar la configuración y la plataforma para mostrar o modificar.  
  
 **Configuración**  
 Especifica las opciones de configuración para mostrar o modificar.  Los valores son **Depurar** \(valor predeterminado\), **Liberar**, **Todas las configuraciones** o una configuración definida por el usuario.  Para obtener más información, consulte [Debug and Release Project Configurations](http://msdn.microsoft.com/es-es/0440b300-0614-4511-901a-105b771b236e).  
  
 **Platform**  
 Especifica la configuración de plataforma para mostrar o modificar.  Los valores son **Cualquier CPU** \(valor predeterminado para aplicaciones [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)]\), **x64**, **ARM**, **x86** o una plataforma definida por el usuario.  Para obtener más información, consulte [Debug and Release Project Configurations](http://msdn.microsoft.com/es-es/0440b300-0614-4511-901a-105b771b236e).  
  
## Página general  
 Utilice las siguientes opciones para establecer las propiedades generales del proyecto.  
  
> [!NOTE]
>  Algunas opciones solo están disponibles en aplicaciones de la Tienda Windows.  
  
 **Ruta de acceso de los resultados**  
 Especifica la ubicación de los archivos de salida para la configuración del proyecto.  La ruta de acceso es relativa. Si escribe una ruta de acceso absoluta, se guarda la ruta de acceso absoluta en el proyecto.  La ruta de acceso predeterminada es bin\\Debug.  
  
 Cuando utiliza las configuraciones de compilación simplificadas, el sistema del proyecto determina si se debe generar una depuración o versión de lanzamiento.  Al hacer clic en **Depurar**, **Iniciar depuración** \(o presionar F5\), la compilación se coloca en la ubicación de depuración sin tener en cuenta la **Ruta de acceso de salida** que especifique.  Sin embargo, el comando **Compilar solución** en el menú **Compilar** la coloca en la ubicación que especifique.  Para habilitar configuraciones de compilación avanzadas, en la barra de menús, elija **Herramientas**, **Opciones**.  En el cuadro de diálogo **Opciones**, expanda **Proyectos y soluciones**, seleccione **General** y, a continuación, desactive la casilla **Mostrar configuraciones de compilación avanzadas**.  Esta opción permite controlar manualmente todos los valores de configuración y si se crea una versión de depuración o lanzamiento.  Para obtener más información, consulte [General, Proyectos y soluciones, Cuadro de diálogo Opciones](http://msdn.microsoft.com/es-es/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
 **Idioma predeterminado**  
 Especifica el idioma predeterminado del proyecto.  La opción de idioma seleccionada en el Panel de control **Reloj, idioma y región** especifica el idioma preferido del usuario.  Al especificar un idioma predeterminado para el proyecto, se asegura de que se utilizan los recursos de idioma predeterminados especificados si el idioma preferido del usuario no coincide con los recursos de idioma proporcionados en la aplicación.  
  
## Página de depuración  
 Utilice las siguientes opciones para establecer las propiedades para depurar el comportamiento en el proyecto.  
  
> [!NOTE]
>  Algunas opciones solo están disponibles en aplicaciones de la Tienda Windows.  
  
 **Depurador para iniciar**  
 Especifica el host predeterminado para el depurador.  
  
-   Seleccione **Equipo Local** para iniciar la aplicación en el equipo host de Visual Studio.  Para obtener más información, consulte [Ejecutar aplicaciones en el equipo local](http://go.microsoft.com/fwlink/?LinkId=234912).  
  
-   Seleccione **Simulator** para iniciar la aplicación en el simulador.  Para obtener más información, consulte [Ejecutar aplicaciones en el simulador](http://go.microsoft.com/fwlink/?LinkId=234913).  
  
-   Seleccione **Equipo remoto** para iniciar la aplicación en un equipo remoto.  Para obtener más información, consulte [Ejecutar aplicaciones en un equipo remoto](http://go.microsoft.com/fwlink/?LinkId=234914).  
  
 **Iniciar aplicación**  
 Especifica si se debe iniciar la aplicación cuando presiona F5 o hace clic en **Depurar**, **Iniciar depuración**.  Seleccione **Sí** para iniciar la aplicación. En caso contrario, seleccione **No**.  Si selecciona **No**, aún puede depurar la aplicación si utiliza un método diferente para iniciarla.  
  
 **Tipo de depurador**  
 Especifica los tipos de código para depurar.  Seleccione **Solo scripts** para depurar código de JavaScript.  Seleccione **Solo administrado** para depurar código administrado por Common Language Runtime.  Seleccione **Solo nativo** para depurar código de C\+\+.  Seleccione **Nativo con Script** para depurar C\+\+ y JavaScript.  Seleccione **Mixto \(administrado y nativo\)** para depurar código administrado y código de C\+\+.  
  
 **Permitir bucle invertido de la red local**  
 Especifica si se permite el acceso a la dirección IP de bucle invertido para probar aplicaciones.  Seleccione **Sí** para permitir el uso de la dirección de bucle invertido si la aplicación cliente se encuentra en el mismo equipo en el que se está ejecutando la aplicación de servidor. En caso contrario, seleccione **No**.  Esta propiedad está disponible solo si la propiedad **Depurador para iniciar** está establecida en **Equipo remoto**.  
  
 **Nombre de equipo**  
 Especifica el nombre del equipo remoto para hospedar al depurador.  Esta propiedad está disponible solo si **Depurador para iniciar** está establecido en **Equipo remoto**.  
  
 **Requerir autenticación**  
 Especifica si el equipo remoto requiere autenticación.  Esta propiedad está disponible solo si **Depurador para iniciar** está establecido en **Equipo remoto**.