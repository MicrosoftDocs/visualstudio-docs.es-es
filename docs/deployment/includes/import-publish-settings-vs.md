
1. En el equipo donde tiene el proyecto ASP.NET abierto en Visual Studio, haga clic en el proyecto en el Explorador de soluciones y elija **publicar**.

1. Si previamente ha configurado ningún perfil de publicación, la **publicar** aparece el panel. Haga clic en **crear nuevo perfil**.

1. En el **elegir un destino de publicación** cuadro de diálogo, haga clic en **importar perfil**.

    ![Elija publicar](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Navegue hasta la ubicación del archivo de configuración de publicación que ha creado en la sección anterior.

1. En el **importar el archivo de configuración de publicación** cuadro de diálogo, vaya a y seleccione el perfil que creó en la sección anterior y haga clic en **abiertos**.

    Visual Studio inicia el proceso de implementación y la ventana de salida muestra el progreso y los resultados.

    Si recibe una implementación de los errores, haga clic en **configuración** para editar la configuración. Modificar la configuración y haga clic en **validar** para probar la nueva configuración. Si no se encuentra el nombre de host, pruebe la dirección IP en lugar del nombre de host en el **Server** y **dirección URL de destino** campos.

    ![Editar la configuración de la herramienta de publicación](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
