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
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "67043463"
---
1. En el equipo remoto, buscar e iniciar el **Remote Debugger** desde el **iniciar** menú. 
   
   Si no tiene permisos administrativos en el equipo remoto, haga clic en el **Remote Debugger** aplicación y seleccione **ejecutar como administrador**. En caso contrario, simplemente iniciarlo con normalidad.

   Si va a adjuntar a un proceso que se está ejecutando como administrador, o se está ejecutando en un usuario diferente de la cuenta (como IIS), haga clic en el **Remote Debugger** aplicación y seleccione **ejecutar como administrador**. Para obtener más información, consulte [ejecutar el depurador remoto como un administrador](../remote-debugging-errors-and-troubleshooting.md#run-the-remote-debugger-as-an-administrator).
   
1. La primera vez que inicie el depurador remoto (o antes de que se ha configurado), el **configuración de depuración remota** aparece el cuadro de diálogo.  
  
    ![Configuración de Remote Debugger](../media/remotedebuggerconfwizardpage.png "configuración del depurador remoto")  
  
1. Si la API de servicios Web de Windows no está instalada, lo que sucede en Windows Server 2008 R2, seleccione el **instalar** botón.  
  
1. Seleccione el tipo de al menos una red que desea usar las herramientas remotas en. Si los equipos están conectados a través de un dominio, debe elegir el primer elemento. Si los equipos están conectados a través de un grupo de trabajo o grupo en el hogar, elija el segundo o tercer elemento según corresponda.  
  
1. Seleccione **Configurar depuración remota** para configurar el firewall e iniciar el depurador remoto.  
  
1. Cuando se complete la configuración de la **Remote Debugger** aparecerá la ventana.
  
    ![Ventana del depurador remoto](../media/remotedebuggerwindow.png "ventana del depurador remoto")
  
    El depurador remoto ahora está esperando una conexión. Utilice el nombre del servidor y el puerto número que se muestra para establecer la configuración de conexión remota en Visual Studio.  
  
Para detener el depurador remoto, seleccione **archivo** > **Exit**. Puede reiniciarlo desde el **iniciar** menú, o desde la línea de comandos:  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```
