---
ms.openlocfilehash: 69f4f4c2b55670d510652b44a203b9f0eafcc53a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "57874495"
---

1. Cierre y vuelva a abrir la consola de administración de IIS para mostrar las opciones de configuración actualizadas en la interfaz de usuario.

2. En IIS, haga clic en el **Sitio web predeterminado**, elija **Implementar** > **Configurar publicación de implementación en Web Deploy**.

    ![Configuración de Web Deploy](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

3. En el cuadro de diálogo **Configurar implementación de publicación en Web Deploy**, examine la configuración.

4. Haga clic en **Configuración**.

    En el panel **Resultados**, el resultado muestra que los derechos de acceso se conceden al usuario especificado y que se ha generado un archivo con una extensión *.publishsettings* en la ubicación que se muestra en el cuadro de diálogo.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    Según la configuración de Windows Server e IIS, verá valores diferentes en el archivo XML. A continuación se detalla alguna información acerca de los valores que verá:

   * El archivo *msdeploy.axd* al que hace referencia el atributo `publishUrl` es un archivo de controlador HTTP generado dinámicamente para Web Deploy. (Para fines de pruebas, `http://myhostname:8172` generalmente funciona bien.)
   * El puerto `publishUrl` se establece en el puerto 8172, que es el valor predeterminado de Web Deploy.
   * El puerto `destinationAppUrl` se establece en el puerto 80, que es el valor predeterminado de IIS.
   * Si no puede conectarse al host remoto en Visual Studio con el nombre de host (en pasos posteriores), pruebe la dirección IP en lugar del nombre de host.

     > [!NOTE]
     > Si va a publicar en IIS que ejecutándose en una máquina virtual de Azure, debe abrir los puertos de IIS y Web Deploy en el grupo Seguridad de red. Para obtener información detallada, consulte [Instalación y ejecución de IIS](/azure/virtual-machines/windows/quick-create-portal#install-web-server).

5. Copie este archivo en el equipo donde se ejecuta Visual Studio.
