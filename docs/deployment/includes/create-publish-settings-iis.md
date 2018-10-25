
1. Cierre y vuelva a abrir la consola de administración de IIS para mostrar las opciones de configuración actualizada en la interfaz de usuario.

2. En IIS, haga clic en el **sitio Web predeterminado**, elija **implementar** > **configurar implementación de publicación en Web**.

    ![Configuración de Web Deploy](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

3. En el **configurar implementación de publicación en Web** diálogo cuadro, examine la configuración.

4. Haga clic en **instalación**.

    En el **resultados** panel, el resultado muestra que los derechos de acceso se concede al usuario especificado y que un archivo con un *.publishsettings* se ha generado la extensión de archivo en la ubicación que se muestra en el cuadro de diálogo cuadro.

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

    Según la configuración de Windows Server e IIS, vea valores diferentes en el archivo XML. Estos son algunos detalles acerca de los valores que se ve:

   * El *msdeploy.axd* archivo hace referenciado en el `publishUrl` atributo es un archivo de controlador HTTP generado dinámicamente para Web Deploy. (Para fines de pruebas `http://myhostname:8172` generalmente funciona bien.)
   * El `publishUrl` puerto se establece en el puerto 8172, que es el valor predeterminado de Web Deploy.
   * El `destinationAppUrl` puerto se establece en el puerto 80, que es el valor predeterminado para IIS.
   * Si no puede conectarse al host remoto en Visual Studio con el nombre de host (en pasos posteriores), pruebe la dirección IP en lugar del nombre de host.

     > [!NOTE]
     > Si va a publicar en IIS que se ejecuta en una máquina virtual de Azure, debe abrir los puertos IIS y Web Deploy en el grupo de seguridad de red. Para obtener información detallada, consulte [instalación y ejecución de IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic).

5. Copie este archivo en el equipo donde se ejecuta Visual Studio.
