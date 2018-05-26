Web Deploy 3.6 para servidores de hospedaje proporciona características de configuración adicionales que permiten la creación de archivo de configuración de publicación de la interfaz de usuario.

1. Si tiene 3.6 de implementación Web ya está instalado en Windows Server, desinstalarlo mediante **el Panel de Control** > **programas** > **desinstalar un programa**.

1. A continuación, instalar 3.6 de implementación Web para los servidores de hospedaje de Windows Server.

    Para instalar Web Deploy para servidores de hospedaje, utilice la [instalador de plataforma Web (WPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Para buscar el vínculo del instalador de plataforma Web de IIS, seleccione **IIS** en el panel izquierdo del administrador del servidor. Haga clic en el servidor y seleccione **Internet Information Services (IIS) Manager**.)

    En el instalador de plataforma Web, encontrará **Web Deploy para servidores de hospedaje** en la pestaña aplicaciones.

1. Si no ha instalado ya **herramientas ni Scripts de administración de IIS**, hágalo ahora.

    Vaya a **seleccionar roles de servidor** > **servidor Web (IIS)** > **herramientas de administración**y, a continuación, seleccione la **secuencias de comandos de administración de IIS Herramientas y** rol, haga clic en **siguiente**y, a continuación, instalar el rol.

    ![Instalar herramientas y Scripts de administración de IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Los scripts y herramientas necesarios para habilitar la generación del archivo de configuración de publicación.

1. (Opcional) Compruebe que Web Deploy se ejecuta correctamente, abra **el Panel de Control > sistema y seguridad > Herramientas administrativas > servicios** y asegúrese de que **servicio Web Deployment Agent** se ejecuta (el nombre del servicio es diferente en versiones anteriores).

    Si el servicio del agente no se está ejecutando, inícielo. Si no está presente en absoluto, vaya a **el Panel de Control > Programas > desinstalar un programa**, buscar **Microsoft Web Deploy <version>** . Elegir **cambio** la instalación y asegúrese de que elige **se instalará en la unidad de disco duro local** para los componentes Web Deploy. Complete los pasos de instalación de cambio.