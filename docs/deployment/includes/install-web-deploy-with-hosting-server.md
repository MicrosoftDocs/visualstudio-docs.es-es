Web Deploy 3.6 para servidores de hospedaje proporciona características de configuración adicionales que permiten la creación del archivo de configuración de publicación de la interfaz de usuario.

1. Si tienes 3.6 de implementación Web ya está instalado en Windows Server, desinstálelo utilizando **Panel de Control** > **programas** > **desinstalar un programa**.

2. A continuación, instale 3.6 de implementación Web para servidores de hospedaje en Windows Server.

    Para instalar Web Deploy para servidores de hospedaje, use el [instalador de plataforma Web (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Para encontrar el vínculo del instalador de plataforma Web de IIS, seleccione **IIS** en el panel izquierdo del administrador del servidor. Haga clic en el servidor y seleccione **Internet Information Services (IIS) Manager**.)

    En el instalador de plataforma Web, encontrará **Web Deploy para servidores de hospedaje** en la pestaña aplicaciones.

3. Si no ha instalado ya **herramientas ni Scripts de administración de IIS**, hágalo ahora.

    Vaya a **seleccionar roles de servidor** > **servidor Web (IIS)** > **las herramientas de administración**y, a continuación, seleccione el **Scripts de administración de IIS Herramientas y** rol, haga clic en **siguiente**y, a continuación, instalar el rol.

    ![Instalar herramientas y Scripts de administración de IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Los scripts y herramientas son necesarios para habilitar la generación del archivo de configuración de publicación.

4. (Opcional) Compruebe que Web Deploy se ejecuta correctamente abriendo **Panel de Control > sistema y seguridad > Herramientas administrativas > servicios** y asegúrese de que **servicio del agente de implementación Web** se está ejecutando (la nombre del servicio es diferente en las versiones anteriores).

    Si no se está ejecutando el servicio del agente, inícielo. Si no está presente en absoluto, vaya a **Panel de Control > Programas > desinstalar un programa**, encontrar **Microsoft Web Deploy <version>** . Elegir **cambio** la instalación y asegúrese de que elige **se instalará en la unidad de disco dura local** para los componentes Web Deploy. Complete los pasos de instalación de cambio.