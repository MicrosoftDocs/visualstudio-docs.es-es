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
ms.openlocfilehash: 252c505260986bd08b5522ba79d1e00a82624241
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942964"
---
Debe tener permisos administrativos en el equipo remoto.  
  
1. Busque la aplicación Depurador remoto. (Busque msvsmon.exe en la ubicación donde se haya instalado o abra el menú Inicio y busque **Remote Debugger**.)
  
    Si se ejecuta el depurador remoto en un servidor remoto, puede haga clic en la aplicación del depurador remoto y elegir **ejecutar como administrador**. Si no se está ejecutando en un servidor remoto, simplemente inícielo con normalidad.
  
2. Al iniciar las herramientas remotas por primera vez (o antes de que se haya configurado), el **configuración de depuración remota** aparece el cuadro de diálogo.  
  
    ![RemoteDebuggerConfWizardPage](../media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Si la API de servicio de Windows no está instalada (que solo se produce en Windows Server 2008 R2), elija el **instalar** botón.  
  
4. Seleccione los tipos de red en los que desea usar las herramientas remotas. Debe seleccionar al menos un tipo de red. Si los equipos están conectados a través de un dominio, debe elegir el primer elemento. Si los equipos están conectados a través de un grupo de trabajo o un grupo en el hogar, debe elegir el segundo o tercer elemento según corresponda.  
  
5. Elija **Configurar depuración remota** para configurar el firewall e iniciar la herramienta.  
  
6. Cuando se completa la configuración, aparecerá la ventana del depurador remoto.
  
    ![RemoteDebuggerWindow](../media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    El depurador remoto ahora está esperando una conexión. Tome nota del nombre del servidor y número de puerto que se muestra, porque debe coincidir con la configuración que posteriormente, usar en Visual Studio.  
  
   Cuando haya terminado la depuración y la necesidad de detener el depurador remoto, haga clic en **archivo > salida** en la ventana. Puede reiniciarlo desde el **iniciar** menú o desde la línea de comandos:  
  
   **\<Directorio de instalación del depurador remoto >\\< x86, x64, ARM, ARM64 o Appx > \msvsmon.exe**.  
