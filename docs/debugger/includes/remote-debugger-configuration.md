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
ms.openlocfilehash: 2e5782c49f26925d9eda81f04653b1a20666c6b1
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68149163"
---
1. En el equipo remoto, busque e inicie **Remote Debugger** en el menú **Inicio**. 
   
   Si no tiene permisos administrativos en el equipo remoto, haga clic con el botón derecho en la aplicación **Remote Debugger** y seleccione **Ejecutar como administrador**. En caso contrario, solo debe iniciarlo de la forma habitual.

   Si tiene previsto realizar una asociación a un proceso que se ejecuta como administrador o se ejecuta en una cuenta de usuario diferente (como IIS), haga clic con el botón derecho en la aplicación **Remote Debugger** y seleccione **Ejecutar como administrador**. Para obtener más información, vea [Ejecución del depurador remoto como administrador](../remote-debugging-errors-and-troubleshooting.md#run-the-remote-debugger-as-an-administrator).
   
1. Al iniciar el depurador remoto por primera vez, o antes de configurarlo, aparecerá el cuadro de diálogo **Configuración de depuración remota**.  
  
    ![Configuración de Remote Debugger](../media/remotedebuggerconfwizardpage.png "Configuración de Remote Debugger")  
  
1. Si la API de servicios web de Windows no está instalada, lo que sucede solo en Windows Server 2008 R2, seleccione el botón **Instalar**.  
  
1. Seleccione al menos un tipo de red en el que desee usar las herramientas remotas. Si los equipos están conectados a través de un dominio, debe elegir el primer elemento. Si los equipos están conectados a través de un grupo de trabajo o un grupo en el hogar, elija el segundo o tercer elemento según corresponda.  
  
1. Seleccione **Configurar depuración remota** para configurar el firewall e iniciar el depurador remoto.  
  
1. Cuando se completa la configuración, aparecerá la ventana **Remote Debugger**.
  
    ![Ventana de Remote Debugger](../media/remotedebuggerwindow.png "Ventana de Remote Debugger")
  
    El depurador remoto ahora está esperando una conexión. Use el nombre del servidor y el número de puerto que se muestran para establecer la configuración de conexión remota en Visual Studio.  
  
Para detener el depurador remoto, seleccione **Archivo** > **Salir**. Puede reiniciarlo desde el menú **Inicio** o desde la línea de comandos:  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
