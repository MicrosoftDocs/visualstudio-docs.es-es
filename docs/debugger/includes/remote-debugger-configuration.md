---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: cfb41cf6274238fef2de9b74496a33fba110e04f
ms.sourcegitcommit: fb73b56d45ebc0386cd4de1a706ba9e20c59daf1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
Debe tener permisos administrativos en el equipo remoto.  
  
1.  Busque la aplicación Depurador remoto. (Buscar msvsmon.exe en la ubicación donde se ha instalado, o abra el menú Inicio y busque **depurador remoto**.)
  
     Si está ejecutando el depurador remoto en un servidor remoto, puede, haga clic en la aplicación del depurador remoto y elegir **ejecutar como administrador**. Si no lo está ejecutando en un servidor remoto, simplemente empiece a él normalmente.
  
3.  Al iniciar las herramientas remotas por primera vez (o antes de que se haya configurado), el **configuración de depuración remota** aparece el cuadro de diálogo.  
  
     ![RemoteDebuggerConfWizardPage](../media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
4.  Si la API de servicio de Windows no está instalada (lo que sucede en Windows Server 2008 R2), elija la **instalar** botón.  
  
5.  Seleccione los tipos de red en los que desea usar las herramientas remotas. Debe seleccionar al menos un tipo de red. Si los equipos están conectados a través de un dominio, debe elegir el primer elemento. Si los equipos están conectados a través de un grupo de trabajo o un grupo en el hogar, debe elegir el segundo o tercer elemento según corresponda.  
  
6.  Elija **configurar la depuración remota** para configurar el firewall e iniciar la herramienta.  
  
7.  Cuando se completa la configuración, aparecerá la ventana del depurador remoto.
  
     ![RemoteDebuggerWindow](../media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
     El depurador remoto está en espera para una conexión. Tome nota del nombre del servidor y el puerto número que se muestra, porque debe coincidir con la configuración que se utiliza posteriormente en Visual Studio.  
  
 Cuando haya terminado de depuración y la necesidad de detener el depurador remoto, haga clic en **archivo > salida** en la ventana. Puede reiniciar desde el **iniciar** menú o desde la línea de comandos:  
  
 **\<Directorio de instalación de Visual Studio > \Common7\IDE\Remote Debugger\\< x86, x64 o Appx > \msvsmon.exe**.  
