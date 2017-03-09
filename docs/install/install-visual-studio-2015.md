---
title: "Instalar Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "vs.about"
helpviewer_keywords: 
  - "Visual Studio, instalación"
  - "instalar Visual Studio"
  - "instalaciones en servidor [Visual Studio]"
  - "Instalación [Visual Studio]"
  - "instalar Visual Studio"
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 177
caps.handback.revision: 150
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Instalar Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En esta página se incluye información detallada para ayudarle con la instalación de Visual Studio 2015, nuestro conjunto integrado de herramientas de productividad para desarrolladores. También hemos incluido vínculos para ayudarle a obtener rápidamente información sobre [características](https://www.visualstudio.com/en-us/news/vs2015-vs.aspx), [ediciones](http://go.microsoft.com/fwlink/?LinkID=242142), [requisitos del sistema](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), [descargas](http://go.microsoft.com/fwlink/?LinkId=517106) y mucho más.  
  
> [!TIP]
>  Para ver información de instalación de versiones anteriores de Visual Studio, haga clic en el vínculo "Otras versiones" de la parte superior de esta página.  
  
## Vínculos rápidos  
 Antes de profundizar en los detalles, se muestra a continuación una lista de los vínculos solicitados con más frecuencia.  
  
|Características|  
|---------------------|  
|Para obtener más información sobre las características nuevas o actualizadas de Visual Studio 2015, vea las notas de la versión de [Visual Studio 2015 RTM](https://www.visualstudio.com/en-us/news/vs2015-vs.aspx) y [Visual Studio 2015 Update 1](https://www.visualstudio.com/news/vs2015-update1-vs).|  
|Para obtener información sobre el contenido disponible en cada edición de Visual Studio de 2015, vea nuestra página [Compare las ofertas de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=242142).|  
|Para ver los requisitos del sistema de cada edición de Visual Studio 2015, vea la página [Compatibilidad de Visual Studio 2015](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs).|  
|Para instalar Visual Studio de 2015, descárguelo desde [Descargas de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=517106), o bien use el medio de instalación suministrado en la caja del producto.|  
|Para encontrar la clave del producto, vea el tema [Cómo: Encontrar la clave de producto de Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md).|  
|Para obtener información sobre las opciones para clientes individuales o empresariales, vea el documento técnico [Licencias de Visual Studio y MSDN](https://www.microsoft.com/download/details.aspx?id=13350).|  
  
##  <a name="custom"></a> Instalación predeterminada frente a Instalación personalizada  
 Cuando se instala Visual Studio de 2015, puede incluir o excluir componentes que usaría diariamente. Esto significa que la instalación predeterminada suele ocupar menos espacio e instalarse más rápido que una instalación personalizada. También significa que muchos componentes instalados de forma predeterminada en versiones anteriores ahora se consideran componentes personalizados que se deben seleccionar de forma explícita en esta versión.  
  
 ![Cuadro de diálogo del programa de instalación de Visual Studio de 2015](../ide/media/vs2015_setup_screen.png "VS2015\_Setup\_screen")  
  
 Entre los componentes personalizados se incluye Visual C\+\+, Visual F\#, SQL Server Data Tools, herramientas y SDK móviles multiplataforma y SDK y extensiones. Puede instalar cualquiera de los componentes personalizados más adelante si no los selecciona durante la configuración inicial.  
  
> [!NOTE]
>  Una instalación personalizada incluye automáticamente los componentes que se encuentran en una instalación predeterminada.  
  
 La lista completa de componentes personalizados es la siguiente:  
  
-   **Lenguajes de programación**  
  
    -   Compiladores, bibliotecas y herramientas de Visual C\+\+  
  
    -   Visual F\#  
  
    -   Python Tools para Visual Studio  
  
-   **Desarrollo web y de Windows**  
  
    -   Herramientas de publicación de ClickOnce  
  
    -   Microsoft SQL Server Data Tools  
  
    -   Microsoft Web Developer Tools  
  
    -   Herramientas de PowerShell para Visual Studio  
  
    -   Kit de desarrollo de Silverlight  
  
    -   Herramientas de desarrollo de aplicaciones universales de Windows  
  
    -   SDK y herramientas de Windows 10  
  
    -   Herramientas de Windows 8.1 y Windows Phone 8.0\/8.1  
  
    -   SDK y herramientas de Windows 8.1  
  
-   **Desarrollo móvil multiplataforma**  
  
    -   Xamarin \(C\# y .NET\)  
  
    -   Apache Cordova \(HTML\/JavaScript\)  
  
    -   Desarrollo móvil de Visual C\+\+ para iOS y Android  
  
-   **SDK y herramientas comunes**  
  
    -   Kit de desarrollo nativo de Android \(R10E, 32 bits\)  
  
    -   SDK de Android  
  
    -   Programa de instalación del SDK de Android \(nivel de API 19 y 21\)  
  
    -   Programa de instalación del SDK de Android \(nivel de API 22\)  
  
    -   Apache Ant \(1.9.3\)  
  
    -   Kit de desarrollo de Java SE \(7.0.550.13\)  
  
    -   Node.js de Joyent  
  
-   **Herramientas comunes**  
  
    -   Git para Windows  
  
    -   Extensiones de GitHub para Visual Studio  
  
    -   Herramientas de extensibilidad de Visual Studio  
  
##  <a name="installing"></a> Instalar Visual Studio  
 Necesita credenciales de administrador para instalar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Sin embargo, no las necesita para usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] después de su instalación.  
  
 La cuenta de administrador local debe tener los siguientes privilegios habilitados para instalar todos los componentes en Visual Studio.  
  
|Nombre para mostrar del objeto de directiva local|Derecho de usuario|  
|-------------------------------------------------------|------------------------|  
|Directorios y archivos de copia de seguridad|SeBackupPrivilege|  
|Programas de depuración|SeDebugPrivilege|  
|Administrar la auditoría y el registro de seguridad|SeSecurityPrivilege|  
  
 Para obtener más información sobre este requisito de la cuenta de administrador local, vea el artículo de Knowledge Base [Se produce un error en la instalación de SQL Server si la cuenta de instalación no tiene ciertos derechos de usuario](https://support.microsoft.com/en-us/kb/2000257).  
  
###  <a name="BKMK_Media"></a> Instalar mediante los discos de instalación  
  
-   Para instalar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], en el directorio raíz del disco de instalación de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ejecute el archivo de instalación de la edición que desee:  
  
    |Edición|Archivo de instalación|  
    |-------------|----------------------------|  
    |Visual Studio Enterprise|vs\_enterprise.exe|  
    |Visual Studio Professional|vs\_professional.exe|  
    |Comunidad de Visual Studio|vs\_community.exe|  
  
###  <a name="BKMK_Website"></a> Instalar mediante una descarga del sitio web del producto  
  
-   Visite [Descargas de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=517106) en el sitio web VisualStudio.com.  
  
###  <a name="BKMK_Offline"></a> Descargar Visual Studio para una instalación sin conexión  
 En la mayoría de los casos, puede instalar Visual Studio desde el sitio de descargas sin problemas. Sin embargo, puede que en algunos casos desee descargar todos los paquetes de actualización antes de la instalación \(por ejemplo, para realizar la instalación en varios equipos o en un equipo sin conexión\). En los pasos siguientes se explica cómo descargar todos los paquetes de actualización necesarios para una instalación sin conexión.  
  
1.  Después de descargar la aplicación ejecutable de actualización desde el sitio web de MSDN en una ubicación del sistema de archivos, ejecute el comando siguiente en un símbolo del sistema: `<executable name> /layout`.  
  
     Este comando descarga todos los paquetes para la instalación.  
  
     Con el conmutador `/layout`, puede descargar casi todos los paquetes de instalación principales, no solo los que se aplican a la máquina de descarga. Este enfoque le proporciona todos los archivos que necesita para ejecutar esta actualización en cualquier parte y puede resultar útil si desea instalar componentes que no se instalaron originalmente.  
  
2.  Después de ejecutar el comando, se le preguntará la ubicación de descarga. Escriba la ubicación y elija **Descargar**.  
  
3.  Cuando la descarga del paquete ha finalizado, debe ver la pantalla de Visual Studio **¡La instalación se realizó correctamente\! Todos los componentes especificados se han adquirido correctamente.**  
  
4.  En la ubicación de archivo especificado, busque el archivo ejecutable y la carpeta package. Esto es todo lo que necesita copiar en una ubicación compartida o en discos de instalación.  
  
    > [!CAUTION]
    >  Actualmente, el SDK de Android no admite una experiencia de instalación sin conexión. Si instala elementos de la instalación del SDK de Android en un equipo que no está conectado a Internet, es posible que se produzca un error en la instalación.  
  
5.  Ahora puede ejecutar la instalación desde la ubicación del archivo o desde los discos de instalación.  
  
###  <a name="BKMK_Virtualized"></a> Instalar Visual Studio en entornos virtualizados  
 **Problemas de vídeo con Hyper\-V**  
  
 Si ejecuta Windows Server 2008 R2 con Hyper\-V habilitado y un adaptador de gráficos acelerado, el sistema puede funcionar despacio.  
  
 Para obtener más información, vea la página siguiente en el sitio web de Microsoft: [El rendimiento de vídeo puede disminuir cuando un equipo basado en Windows Server 2008 o Windows Server 2008 R2 tiene habilitado el rol de Hyper\-V y tiene instalado un adaptador de pantalla acelerado](http://go.microsoft.com/fwlink/?LinkID=231084).  
  
 **Emular dispositivos con Hyper\-V**  
  
 Al instalar Visual Studio 2015 en hardware real sin virtualización, puede elegir características que habilitan la emulación de dispositivos Windows y Android mediante Hyper\-V. Al instalar en Hyper\-V, no podrá emular los dispositivos Windows o Android. Esto es así porque los emuladores son máquinas virtuales y actualmente no es posible hospedar una máquina virtual dentro de otra. La solución alternativa consiste en disponer de dispositivos reales Windows o Android en los que pueda implementar directamente la aplicación y depurarla.  
  
## Usar parámetros de la línea de comandos  
 Al ejecutar la aplicación de instalación, puede utilizar los parámetros de la línea de comandos siguientes, que no distinguen mayúsculas de minúsculas.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|**\/?**<br /><br /> **\/help**<br /><br /> **\/h**|Muestra los parámetros de la línea de comandos.|  
|**\/AddRemoveFeatures**|Especifica qué características se van a agregar o quitar del producto instalado.|  
|**\/AdminFile** *AdminDeployment.xml*|Instala Visual Studio usando el archivo de datos que especificó para la instalación administrativa.|  
|**\/CEIPConsent**|Consiente la recopilación de información para mejorar la experiencia del cliente de acuerdo con la directiva de privacidad del producto.|  
|**\/ChainingPackage** *BundleName*|Especifica qué agrupación está encadenando este paquete. También puede usarse para especificar una cohorte para la experiencia de mejora del cliente.|  
|**\/CreateAdminFile \<filename\>**|Especifica la ubicación para crear un archivo de control que se puede usar con \/AdminFile|  
|**\/CustomInstallPath** *InstallationDirectory*|Instala todos los paquetes que se pueden volver a establecer como destino en el directorio especificado.|  
|**\/ForceRestart**|Reinicia siempre el equipo después de la instalación.|  
|**\/full**|Instala todas las características del producto.|  
|**\/InstallSelectableItems \<item name 1\>\[;\<item name 2\>\]**|Lista de elementos del árbol de selección que se comprueba en la pantalla de selección del Asistente para la instalación.|  
|**\/l**<br /><br /> **\/Log** *Filename*|Especifica una ubicación para el archivo de registro.|  
|**\/layout** *Directory*|Copia los archivos del disco de instalación al directorio especificado.|  
|**\/NoCacheOnlyMode**|Impide que se rellene automáticamente la memoria caché del paquete.|  
|**\/NoRefresh**|Impide comprobar la existencia de versiones más recientes de este producto para versiones actualizadas necesarias o recomendadas.|  
|**\/norestart**|Impide que la aplicación de instalación reinicie el equipo durante o después de la instalación. Vea la sección Códigos de retorno de la [Guía del administrador de Visual Studio](../install/visual-studio-administrator-guide.md) para buscar los códigos de retorno.|  
|**\/noweb**|Impide la instalación desde Internet.|  
|**\/OverrideFeedUri \<path to feed file\>**|Ruta de acceso a una fuente local y externa que describe los elementos de software|  
|**\/ProductKey**<br /><br /> *ProductKey*|Establece una clave del producto personalizada que no contiene ningún guion y no tiene más de 25 caracteres.|  
|**\/PromptRestart**|Pregunta al usuario antes de reiniciar el equipo.|  
|**\/q**<br /><br /> **\/quiet**<br /><br /> **\/s**<br /><br /> **\/silent**|Suprime la interfaz de usuario \(IU\) para la aplicación de instalación. Si Visual Studio ya está instalado y no especifica ningún parámetro excepto este, la aplicación de instalación se ejecuta en modo de mantenimiento.|  
|**\/qb**<br /><br /> **\/passive**|Muestra el progreso pero no espera datos proporcionados por el usuario.|  
|**\/repair**|Repara Visual Studio.|  
|**\/SuppressRefreshPrompt**|Evita mostrar que el cuadro de diálogo de actualización disponible en el Asistente para la instalación, de modo que el Asistente para la instalación aceptará automáticamente cualquier versión actualizada necesaria o recomendada.|  
|**\/u**<br /><br /> **\/Uninstall**|Desinstala [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|**\/Uninstall \/Force**<br /><br /> **\/u \/force**|Desinstala Visual Studio y todas las características que se comparten con otros productos. **Warning:**  Si utiliza este parámetro, otros productos instalados en el mismo equipo pueden dejar de funcionar correctamente.|  
  
 Al ejecutar la instalación desde la línea de comandos, es conveniente capturar y procesar el código de retorno para una mejor experiencia de la línea de comandos.  Para obtener más información, vea [Guía del administrador de Visual Studio](../install/visual-studio-administrator-guide.md).  
  
##  <a name="troubleshooting"></a> Solucionar problemas de la instalación  
 Use estos recursos para obtener ayuda con los problemas de instalación y configuración:  
  
-   [Foro sobre la configuración e instalación de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=151190). Consulte las preguntas y respuestas de otras personas en la comunidad de Visual Studio. Si no encuentra lo que necesita, haga sus propias preguntas.  
  
-   [Sitio web Soporte de Microsoft para Visual Studio](http://go.microsoft.com/fwlink/?LinkID=251019). Lea los artículos de Knowledge Base \(KB\) y póngase en contacto con el servicio de soporte técnico de Microsoft para obtener información sobre los problemas con la instalación de Visual Studio.  
  
-   En el caso de las versiones de Visual Studio 2015, puede notificar su problema mediante el sitio de Connect en [https:\/\/connect.microsoft.com\/visualstudio](https://connect.microsoft.com/visualstudio).  
  
     Es mejor si su problema incluye los registros de instalación. Puede preparar los registros para el informe de problemas con Microsoft Visual Studio y la herramienta de recopilación de registros de .NET Framework, tal como se describe en los pasos siguientes.  
  
    1.  Descargue la herramienta de diagnóstico de instalación desde [http:\/\/aka.ms\/vscollect](http://aka.ms/vscollect).  
  
    2.  Desde un símbolo del sistema con privilegios elevados, ejecute el programa collect.exe.  
  
    3.  Una vez finalizado el programa collect.exe, capture el archivo vslogs.cab desde el directorio Temp y cárguelo en el informe de problemas.  
  
##  <a name="enterprise"></a> Implementación en una red empresarial  
 Para obtener información sobre cómo depurar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a través de una red, vea [Guía del administrador de Visual Studio](../install/visual-studio-administrator-guide.md).  
  
##  <a name="afterInstalling"></a> Después de instalar Visual Studio  
 Después de instalar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], se recomienda registrar su copia del producto.  
  
###  <a name="register"></a> Registrar Visual Studio  
  
##### Para registrar Visual Studio  
  
1.  En la barra de menús, elija **Ayuda**, **Acerca de**.  
  
     El cuadro de diálogo **Acerca de** muestra el número de identificación del producto \(PID\). Para registrar el producto, necesitará el PID y las credenciales de cuenta de Windows \(por ejemplo, una dirección de correo electrónico de Hotmail o Outlook.com y la contraseña\).  
  
2.  En la barra de menús, elija **Ayuda**, **Registrar producto**.  
  
###  <a name="helpContent"></a> Instalar contenido de ayuda sin conexión  
 Después de instalar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puede descargar contenido de ayuda adicional para que esté disponible sin conexión.  
  
##### Para instalar o desinstalar el contenido de la Ayuda  
  
1.  En la barra de menús de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], elija **Ayuda**, **Agregar y quitar contenido de la Ayuda**.  
  
2.  En la pestaña **Administrar contenido** del **Visor de Ayuda de Microsoft**, seleccione el origen de instalación del contenido de la Ayuda.  
  
3.  Si está buscando una colección de Ayuda específica, escriba el nombre o una palabra clave en el cuadro de texto **Buscar** y presione Intro.  
  
4.  Al lado del nombre de la colección de Ayuda que desee, elija el vínculo **Agregar** o **Quitar**.  
  
5.  Elija el botón de **Actualizar**.  
  
 Para más información sobre la ayuda sin conexión, vea el artículo de [ayuda del visor de Ayuda 2.2 de Microsoft](../ide/microsoft-help-viewer.md).  
  
###  <a name="repair"></a> Reparar Visual Studio  
  
##### Para reparar Visual Studio  
  
1.  En el **Panel de control**, en la página **Programas y características**, elija la edición del producto que desea reparar y, a continuación, elija **Cambiar**.  
  
2.  En el Asistente para la instalación, elija **Reparar**, elija **Siguiente** y siga las instrucciones restantes.  
  
##### Para reparar Visual Studio en los modos silencioso o pasivo \(es decir, reparar desde el origen\)  
  
1.  En el equipo donde está instalado Visual Studio, abra el símbolo del sistema de Windows.  
  
2.  Escriba los parámetros siguientes:  
  
     *DVDRoot* \\\<Archivo de instalación\> \<\/quiet&#124;\/passive\> \[\/norestart\]\/Repair  
  
###  <a name="optionalComponents"></a> Instalar elementos seleccionables  
  
##### Para instalar elementos seleccionables  
  
1.  En el **Panel de control**, en la página **Programas y características**, elija la edición del producto a la que desea agregar uno o más componentes y, a continuación, elija **Cambiar**.  
  
2.  En el Asistente para la instalación, elija **Modificar** y elija los componentes que desea instalar.  
  
3.  Elija **Siguiente** y siga las instrucciones restantes.  
  
###  <a name="serviceReleases"></a> Buscar versiones Service Release y actualizaciones del producto  
 Visual Studio no actualiza automáticamente las extensiones al realizar la actualización desde versiones anteriores, porque no todas las extensiones son compatibles. Debe reinstalar las extensiones desde la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=178891) o el editor de software.  
  
##### Para comprobar automáticamente si hay actualizaciones Service Release  
  
1.  En la barra de menús, elija **Herramientas**, **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones**, expanda **Entorno** y, a continuación, seleccione **Extensiones y actualizaciones**. Asegúrese de que la casilla **Buscar actualizaciones automáticamente** está activada y haga clic en **Aceptar**.  
  
##  <a name="uninstalling"></a> Desinstalar Visual Studio  
 Use los procedimientos siguientes para desinstalar Visual Studio 2015.  
  
#### Para desinstalar Visual Studio  
  
1.  En el **Panel de control**, en la página **Programas y características**, elija la edición del producto que desea desinstalar y, a continuación, elija **Cambiar**.  
  
2.  En el Asistente para la instalación, elija **Desinstalar**, elija **Sí** y siga las instrucciones restantes del asistente.  
  
#### Para desinstalar Visual Studio en los modos silencioso o pasivo \(es decir, desinstalar desde el origen\)  
  
1.  En el equipo donde está instalado Visual Studio, abra el símbolo del sistema de Windows.  
  
2.  Escriba los parámetros siguientes:  
  
     *DVDRoot* \\\<Archivo de instalación\> \<\/quiet&#124;\/passive\> \[\/norestart\]\/uninstall  
  
 Si no puede desinstalar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mediante la utilidad de desinstalación, puede realizar una desinstalación manual quitando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y, a continuación, quitando los componentes relacionados. Para más información, vea el artículo [Cómo desinstalar Visual Studio](https://support.microsoft.com/en-us/kb/2771441) artículo de Microsoft Knowledge Base \(KB\) o la publicación [Removing Visual Studio components left behind after an uninstall](http://blogs.msdn.com/b/heaths/archive/2015/07/17/removing-visual-studio-components-left-behind-after-an-uninstall.aspx) \(Quitar componentes de Visual Studio que permanecen en el equipo tras la desinstalación\) en el sitio web Microsoft Server & Tools Blogs \(Blogs de herramientas y servidores de Microsoft\).  
  
##  <a name="relatedTopics"></a> Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Instalar distintas versiones de Visual Studio en paralelo](../Topic/Installing%20Visual%20Studio%20Versions%20Side-by-Side.md)|Proporciona información sobre cómo instalar varias versiones de Visual Studio en el mismo equipo.|  
|[Biblioteca de imágenes de Visual Studio](../designers/the-visual-studio-image-library.md)|Proporciona información sobre cómo instalar gráficos que se pueden utilizar en las aplicaciones de Visual Studio.|  
|[Guía del administrador de Visual Studio](../install/visual-studio-administrator-guide.md)|Proporciona información sobre las opciones de implementación de Visual Studio.|  
|[Instalar varias versiones de idioma de Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)|Proporciona información sobre cómo instalar diferentes versiones de idioma de Visual Studio.|  
|[Cómo: Encontrar la clave de producto de Visual Studio](../install/how-to-locate-the-visual-studio-product-key.md)|Proporciona información sobre cómo buscar la clave del producto para su instalación de Visual Studio.|  
|[Introducción](../ide/get-started-developing-with-visual-studio.md)|Vínculos a documentos que pueden ayudarle a utilizar Visual Studio eficazmente.|  
  
## Vea también  
 [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3)