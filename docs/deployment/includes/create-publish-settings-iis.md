
1. Cierre y vuelva a abrir la consola de administración de IIS para mostrar las opciones de configuración actualizada en la interfaz de usuario.

1. En IIS, haga clic en el **sitio Web predeterminado**, elija **implementar** > **configurar implementar publicación en Web**.

    ![Establecer la configuración de Web Deploy](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

1. En el **configurar implementar publicación en Web** diálogo cuadro, examine la configuración.

1. Haga clic en **el programa de instalación**.

    En el **resultados** el panel, el resultado muestra que los derechos de acceso se concede al usuario especificado y que un archivo con un *.publishsettings* extensión de archivo se ha generado desde la ubicación que aparece en el cuadro de diálogo cuadro.

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

    Según la configuración de IIS y Windows Server, vea valores diferentes en el archivo XML. Estos son algunos detalles acerca de los valores que se ven:

    * El *msdeploy.axd* archivo mencionado en el `publishUrl` atributo es un archivo de controlador HTTP generado de forma dinámica para Web Deploy. (Para realizar pruebas, `http://myhostname:8172` generalmente también funciona.)
    * El `publishUrl` puerto se establece en el puerto 8172, que es el valor predeterminado de Web Deploy.
    * El `destinationAppUrl` puerto se establece en el puerto 80, que es el valor predeterminado de IIS.
    * Si no puede conectarse al host remoto en Visual Studio usando el nombre de host (en pasos posteriores), pruebe la dirección IP en lugar del nombre de host.

    > [!NOTE]
    > Si va a publicar en IIS que se ejecuta en una máquina virtual de Azure, debe abrir los puertos IIS y Web Deploy en el grupo de seguridad de red. Para obtener información detallada, vea [instale y ejecute IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic).

1. Copie este archivo en el equipo donde se ejecuta Visual Studio.
