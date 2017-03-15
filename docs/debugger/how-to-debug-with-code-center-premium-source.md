---
title: "C&#243;mo: Depurar c&#243;digo fuente con Code Center Premium | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Code Center Premium"
  - "depurar [Visual Studio], Code Center Premium"
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# C&#243;mo: Depurar c&#243;digo fuente con Code Center Premium
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Con el depurador de [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], puede depurar código fuente compartido seguro de Microsoft MSDN Code Center Premium.  
  
 En este tema se explica cómo configurar y depurar el código fuente de Code Center Premium en Visual Studio.  
  
### Para preparar la depuración con Code Center Premium  
  
1.  Conecte el lector de SmartCard e inserte la tarjeta que obtuvo en la Iniciativa de código fuente compartido.  
  
2.  Inicie Visual Studio.  
  
3.  En el menú **Herramientas**, haga clic en **Opciones**.  
  
4.  En el cuadro de diálogo **Opciones**, abra el nodo **Depuración** y haga clic en **General**.  
  
5.  Desactive la casilla **Habilitar Solo mi código \(solo administrado\)**.  
  
6.  Seleccione **Habilitar compatibilidad de servidor de origen**.  
  
7.  Desactive **Es necesario que los archivos de código fuente coincidan con la versión original**.  
  
8.  Bajo el nodo **Depuración**, haga clic en **Símbolos**.  
  
9. En el cuadro de **Ubicaciones de archivos de símbolos \(.pdb\)**, desactive la casilla **Servidores de símbolos de Microsoft** y agregue las siguientes ubicaciones:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Asegúrese de incluir la barra diagonal final **\/**al final de la ruta de acceso.  
  
     Mueva estas ubicaciones a la parte superior de la lista para asegurarse de que estos símbolos se cargan en primer lugar.  
  
    > [!NOTE]
    >  Estas ubicaciones de Code Center Premium deben enumerarse primero de modo que sean las primeras ubicaciones que se cargan.  En Visual Studio 2010, no puede mover ningún servidor situado encima de la entrada **Servidores de símbolos de Microsoft**; ese es el motivo por el que se debe desactivar la casilla.  
    >   
    >  Para cargar símbolos de Microsoft durante una sesión de depuración, haga lo siguiente:  
    >   
    >  1.  En el menú **Depurar**, elija **Ventanas** y, a continuación, seleccione **Módulos**.  
    > 2.  Seleccione el módulo del que desee símbolos y, a continuación, abra el menú contextual.  Elija **Cargar símbolos desde** y, a continuación, seleccione **Servidores de símbolos de Microsoft**.  
  
10. En el cuadro **Almacenar símbolos en caché desde los servidores de símbolos a este directorio**, escriba una ubicación como `C:\symbols` en la que Code Center Premium pueda almacenar en caché los símbolos.  Almacenar en caché los símbolos puede mejorar significativamente el rendimiento durante la depuración.  
  
     Si tiene dificultades para depurar el código fuente con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] después de completar este procedimiento, compruebe la ubicación de los archivos almacenados en caché previamente y los archivos de símbolos anticuados.  Quite los archivos de símbolos anticuados.  
  
11. Haga clic en **Aceptar**.  
  
12. Reinicie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para asegurarse de que se conserva la configuración.  
  
### Para depurar el código fuente utilizando Asociar al proceso  
  
1.  Conecte el lector de SmartCard e inserte la tarjeta que obtuvo en la Iniciativa de código fuente compartido.  
  
2.  Inicie Visual Studio.  
  
3.  Abra el proyecto de Visual Studio.  
  
4.  En el menú **Herramientas**, haga clic en **Asociar al proceso**.  
  
5.  En el cuadro de diálogo **Asociar al proceso**, haga clic en **Seleccionar**.  
  
6.  En el cuadro de diálogo **Seleccionar tipo de código**, en **Depurar estos tipos de código**, seleccione **Nativo**, **Administrado** y **Administrado \(v4.0\)**.  
  
7.  Haga clic en **Aceptar** para descartar el cuadro de diálogo **Seleccionar tipo de código**.  
  
8.  En el cuadro de **Procesos disponibles**, seleccione el proceso que desea depurar.  
  
9. Haga clic en **Asociar**.  
  
10. Cuando le soliciten que confirme el certificado, haga clic en **Aceptar**.  A continuación, escriba su PIN.  Acepte los términos de uso de Code Center Premium, si se lo piden.  
  
     Descargar los símbolos puede tardar mucho tiempo, dependiendo de la velocidad de la red.  La barra de estado indicará cuando se han descargado correctamente todos los símbolos.  
  
11. Repita los pasos de Asociar al proceso para todos los proyectos administrados de la solución.  
  
### Para depurar el código fuente de una solución existente  
  
1.  En el **Explorador de soluciones**, abra el menú contextual de la solución y, a continuación, elija **Propiedades**.  
  
2.  En el cuadro de diálogo Páginas de propiedades de la solución, seleccione **Depurar archivos de código fuente**, en el nodo **Propiedades comunes**.  
  
3.  Agregue la siguiente ubicación a la lista **Directorios que contienen código fuente**:  
  
     `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
    > [!NOTE]
    >  Asegúrese de incluir la barra diagonal final **\/**al final de la ruta de acceso.  
  
4.  Para cada proyecto administrado de la solución, haga lo siguiente  
  
    1.  En el Explorador de soluciones, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
    2.  Seleccione **Depurar** y, a continuación, elija **Habilitar depuración de código no administrado**.  
  
### Para depurar la solución con el código fuente de Code Center Premium  
  
1.  En la clase `Package`, establezca un punto de interrupción en el constructor del paquete.  
  
2.  En el menú `Debug`, haga clic en **Iniciar depuración**.  
  
3.  Cuando se alcance el punto de interrupción en el constructor del paquete, vaya a la ventana **Pila de llamadas** y haga clic con el botón secundario en el marco de pila del ensamblado del que desea cargar símbolos y, a continuación, haga clic en **Cargar símbolos**.  
  
     Haga doble clic en el marco de la llamada para cargar el código fuente.  
  
### Para examinar el código fuente en Code Center Premium  
  
1.  Conecte el lector de SmartCard e inserte la tarjeta que obtuvo en la Iniciativa de código fuente compartido.  
  
2.  Inicie Internet Explorer y escriba la siguiente dirección URL: `https://codepremium.msdn.microsoft.com`  
  
3.  Busque el código fuente que desea.  
  
## Vea también  
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Code Center Premium](http://www.microsoft.com/resources/sharedsource/ccp.mspx)