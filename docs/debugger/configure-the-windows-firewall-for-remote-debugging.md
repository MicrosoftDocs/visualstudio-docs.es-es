---
title: "Configurar el Firewall de Windows para la depuraci&#243;n remota | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Configurar el Firewall de Windows para la depuraci&#243;n remota
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tema se describe cómo configurar el firewall para habilitar la depuración remota en equipos que ejecutan los sistemas operativos siguientes:  
  
-   Windows 7  
  
-   Windows 8\/8.1  
  
-   Windows 10  
  
-   Windows Server 2008 \(R2\)  
  
-   Windows Server 2012  
  
-   Windows Server 2012 R2  
  
 Si la red en la que está realizando la depuración no está protegida por un firewall, esta configuración no es necesaria. De lo contrario, el equipo que hospeda Visual Studio y el equipo remoto que se va a depurar requerirán cambios en la configuración del firewall.  
  
 **IPSec** Si la red requiere que la comunicación se realice con IPSec, debe abrir puertos adicionales en el equipo host de Visual Studio y en el equipo remoto.  
  
 **Servidor web** Si va a realizar la depuración de un servidor web remoto, debe abrir un puerto adicional en el equipo remoto.  
  
 Tenga en cuenta que ambos equipos no tienen que ejecutar el mismo sistema operativo. Por ejemplo, el equipo de Visual Studio puede ejecutar Windows 10 y el equipo remoto puede ejecutar Windows Server 2012 R2.  
  
## Para configurar el firewall de Windows en el equipo de Visual Studio  
 Las instrucciones para configurar el firewall de Windows varían ligeramente en los distintos sistemas operativos. En Windows 7 o Windows Server 2008, se usa la palabra **programa**; mientras que en Windows 8\/8.1, Windows 10 y Windows Server 2012 se usa la palabra **aplicación**.  En los pasos siguientes se usará la palabra **aplicación**.  
  
1.  Abra la página del Firewall de Windows. \(En el cuadro de búsqueda del menú **Inicio**, escriba **Firewall de Windows**\).  
  
2.  Haga clic en **Permitir una aplicación o una característica a través de Firewall de Windows**.  
  
3.  En la lista **Aplicaciones y características permitidas:**, busque **Detección del depurador remoto de Visual Studio**. Si aparece en la lista, asegúrese de que está seleccionada y de que también estén seleccionados uno o varios tipos de red.  
  
4.  Si no aparece **Detección del depurador remoto de Visual Studio**, haga clic en **Permitir otra aplicación**. Si aún no ve la opción en la ventana **Agregar una aplicación**, haga clic en **Examinar** y vaya a **\<directorio de instalación de Visual Studio\>\\Common7\\IDE\\Remote Debugger**. Busque la carpeta correspondiente de la aplicación \(x86, x64, Appx\) y, a continuación, seleccione **msvsmon.exe**. A continuación, haga clic en **Agregar**.  
  
5.  En la lista **Aplicaciones y características permitidas**, busque **Monitor de depuración remota de Visual Studio**. Active uno o más tipos de red \(**dominio, doméstica\/de trabajo \(privada\) o pública**\) para la comunicación con el monitor de depuración remota. Los tipos deben incluir la red a la que está conectado el equipo de Visual Studio.  
  
## Para abrir un puerto en el equipo de Visual Studio para habilitar la detección  
 Debe permitir el puerto UDP 3702 entrante para permitir la detección de los equipos que ejecutan el depurador remoto. Para agregarlo, vea Cómo configurar puertos en un firewall.  
  
## Para configurar el firewall de Windows del equipo remoto para la depuración remota  
 Los componentes de depuración remota pueden instalarse en el equipo remoto o ejecutarse desde un directorio compartido. El firewall del equipo remoto debe configurarse en ambos casos. Los componentes de depuración remota se encuentra en:  
  
 **\<directorio de instalación de Visual Studio\>\\Common7\\IDE\\Remote Debugger**  
  
 Las instrucciones para configurar el firewall de Windows varían ligeramente en los distintos sistemas operativos. En Windows 7 o Windows Server 2008, se usa la palabra **programa**; mientras que en Windows 8\/8.1, Windows 10 y Windows Server 2012 se usa la palabra **aplicación**.  En los pasos siguientes se usará la palabra **aplicación**.  
  
1.  Abra la página del Firewall de Windows. \(En el cuadro de búsqueda del menú **Inicio**, escriba **Firewall de Windows**\).  
  
2.  Haga clic en **Permitir una aplicación o una característica a través de Firewall de Windows**.  
  
3.  En la lista **Aplicaciones y características permitidas**, busque **Monitor de depuración remota de Visual Studio**. Si aparece en la lista, asegúrese de que está seleccionada y de que también estén seleccionados uno o varios tipos de red.  
  
4.  Si no aparece el **Monitor de depuración remota de Visual Studio** en la lista, haga clic en **Permitir otra aplicación**. Si aún no ve la opción en la ventana **Agregar una aplicación**, haga clic en **Examinar** y vaya a **\<directorio de instalación de Visual Studio\>\\Common7\\IDE\\Remote Debugger**. Busque la carpeta correspondiente de la aplicación \(x86, x64, Appx\) y, a continuación, seleccione **msvsmon.exe**. A continuación, haga clic en **Agregar**.  
  
5.  En la lista **Aplicaciones permitidas**, busque **Monitor de depuración remota de Visual Studio**. Active uno o más tipos de red \(**dominio, doméstica\/de trabajo \(privada\) o pública**\) para la comunicación con el monitor de depuración remota. Los tipos deben incluir la red a la que está conectado el equipo de Visual Studio.  
  
## Puertos en el equipo remoto que habilitan la depuración remota  
  
|||||  
|-|-|-|-|  
|**Puertos**|**Entrante\/saliente**|**Protocolo**|**Descripción**|  
|3702|Saliente|UDP|Necesario para la detección del depurador remoto|  
|4020||TCP|Para VS 2015. El número de puerto se incrementa en 2 para cada versión de Visual Studio. Para más información, vea Asignaciones de puerto de depurador remoto de Visual Studio.|  
|4021||TCP|Para VS 2015. El número de puerto se incrementa en 2 para cada versión de Visual Studio. Para más información, vea Asignaciones de puerto de depurador remoto de Visual Studio.|  
  
## Puertos en el equipo remoto que permiten la depuración remota con el modo de compatibilidad administrado o nativo  
  
|||||  
|-|-|-|-|  
|**Puertos**|**Entrante\/saliente**|**Protocolo**|**Descripción**|  
|135, 139, 445|Saliente|TCP|Obligatorio.|  
|137, 138|Saliente|UDP|Obligatorio.|  
|500, 4500|Saliente|UDP|Necesario si la directiva de dominio exige que la comunicación de red se realice a través de IPSec.|  
|80|Saliente|TCP|Necesario para la depuración en el servidor web.|  
  
## Cómo configurar puertos en el Firewall de Windows  
  
1.  En el menú **Inicio**, busque **Firewall de Windows con seguridad avanzada**.  
  
2.  Haga clic en **Reglas de entrada** o **Reglas de salida** y, a continuación, haga clic en **Nueva regla** en la lista **Acciones**.  
  
3.  En la página **Tipo de regla**, seleccione **Puerto** y, a continuación, haga clic en **Siguiente**.  
  
4.  En la página **Protocolo y puertos** seleccione el protocolo del puerto \(TCP o UDP\). Seleccione **Puertos locales específicos** y escriba uno o más números de puerto que desea habilitar para el protocolo. Separe los números con comas. Después, haga clic en **Siguiente**.  
  
5.  En la página **Acción**, seleccione **Permitir la conexión** y, a continuación, haga clic en **Siguiente**.  
  
6.  En la página **Perfil** seleccione uno o más tipos de red para habilitar para el puerto. Los tipos seleccionados deben incluir la red a la que está conectado el equipo remoto. Después, haga clic en **Siguiente**.  
  
7.  En la página **Nombre**, escriba un nombre para la regla y, a continuación, haga clic en **Finalizar**.  
  
8.  Debería ver la nueva regla en la lista **Reglas de entrada** o **Reglas de salida**.  
  
## Vea también  
 [Depuración remota](../debugger/remote-debugging.md)