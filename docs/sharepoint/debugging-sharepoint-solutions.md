---
title: "Depurar soluciones de SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.WebConfigModificationDialog"
  - "VS.SharePointTools.Project.DebuggingNotEnabled"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, depurar"
ms.assetid: 5120f21e-4c27-4906-b982-85e9cd5170e6
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Depurar soluciones de SharePoint
  Puede depurar las soluciones de SharePoint utilizando el depurador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Al iniciar la depuración, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] implementa los archivos de proyecto en el servidor de SharePoint y, a continuación, abre una instancia del sitio de SharePoint en el explorador web.  En las secciones siguientes se explica cómo depurar aplicaciones de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [Habilitar la depuración](#EnableDebug)  
  
-   [Depuración F5 y proceso de implementación](#Deployment)  
  
-   [Características de proyecto de SharePoint](#Features)  
  
-   [Depurar flujos de trabajo](#Workflow)  
  
-   [Depurar receptores de eventos de características](#FeatureEvents)  
  
-   [Habilitar la información de depuración mejorada](#EnhancedDebug)  
  
##  <a name="EnableDebug"></a> Habilitar la depuración  
 Cuando se depura por primera vez una solución de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], un cuadro de diálogo advierte de que el archivo web.config no está configurado para habilitar la depuración. \(Se crea el archivo web.config al instalar el servidor de SharePoint.  Para obtener más información, vea [Trabajar con archivos Web.config](http://go.microsoft.com/fwlink/?LinkID=149266).\) El cuadro de diálogo da la opción de ejecutar el proyecto sin depurar o modificar el archivo web.config para habilitar la depuración.  Si elige la primera opción, el proyecto se ejecuta normalmente.  Si elige la segunda opción, el archivo web.config se configura para:  
  
-   Activar la pila de llamadas \(`CallStack="true"`\)  
  
-   Deshabilitar los errores personalizados en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\(`<customErrors mode="Off" />`\)  
  
-   Habilitar la depuración de compilación \(`<compilation debug="true">`\)  
  
 A continuación se puede ver el archivo web.config resultante:  
  
```  
  
<configuration>  
    ...  
    <SharePoint>  
        <SafeMode MaxControls="200"  
            CallStack="true"  
            DirectFileDependencies="10"  
            TotalFileDependencies="50"  
            AllowPageLevelTrace="false">  
            ...  
        </SafeMode>  
    ...  
    </SharePoint>  
    <system.web>  
        ...  
        <customErrors mode="Off" />  
        ...  
        <compilation debug="true">  
        ...  
        </compilation>  
        ...  
    </system.web>  
    ...  
</configuration>  
```  
  
 Para revertir los cambios y deshabilitar la depuración, cambie el [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] siguiente en el archivo web.config:  
  
-   Desactivar la pila de llamadas \(`CallStack="false"`\)  
  
-   Habilitar errores personalizados en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]\(`<customErrors mode="On" />`\)  
  
-   Deshabilitar la depuración de compilación \(`<compilation debug="false">`\)  
  
##  <a name="Deployment"></a> Depuración F5 y proceso de implementación  
 Cuando se ejecuta un proyecto de SharePoint en modo de depuración, el proceso de implementación de SharePoint realiza las tareas siguientes:  
  
1.  Ejecuta los comandos anteriores a la implementación personalizables.  
  
2.  Crea un archivo \(.wsp\) de solución web mediante comandos de [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)].  El archivo .wsp incluye todos los archivos y características necesarios.  Para obtener más información, vea [Introducción a las soluciones](http://go.microsoft.com/fwlink/?LinkID=128154).  
  
3.  Si la solución de SharePoint es una solución de granja, recicla el grupo de aplicaciones de [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] para la [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] del sitio especificado.  Este paso libera los archivos bloqueados por el proceso de trabajo de [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)].  
  
4.  Si ya existe una versión anterior del paquete, la retira de las características y los archivos del archivo .wsp.  Este paso desactiva las características, desinstala el paquete de la solución y, a continuación, lo elimina del servidor de SharePoint.  
  
5.  Instala la versión actual de las características y archivos en el archivo .wsp.  Este paso agrega e instala la solución en el servidor de SharePoint.  
  
6.  Para los flujos de trabajo, instala el ensamblado del flujo de trabajo.  Puede cambiar su ubicación mediante la propiedad *Assembly Location*.  
  
7.  Activa la característica del proyecto en SharePoint si el ámbito es Sitio o Web.  No se activan las características de los ámbitos de aplicación web y granja de servidores.  
  
8.  Para los flujos de trabajo, asocia el flujo de trabajo a la biblioteca, lista o sitio de SharePoint que seleccionó en el **Asistente para personalización de SharePoint**.  
  
    > [!NOTE]  
    >  Esta asociación solo se produce si seleccionó **¿Asociar el flujo de trabajo automáticamente?** en el asistente.  
  
9. Ejecuta los comandos posteriores a la implementación personalizables.  
  
10. Adjunta el depurador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] al proceso de [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] \(w3wp.exe\).  Si el tipo de proyecto permite cambiar la propiedad *Sandboxed Solution* y su valor está establecido en **true**, el depurador se adjuntará a un proceso diferente \(SPUCWorkerProcess.exe\).  Para obtener más información, vea [Consideraciones sobre las soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
11. Inicia el depurador de JavaScript si la solución de SharePoint es una solución de granja.  
  
12. Muestra la biblioteca, lista o página de sitio adecuada en el explorador web.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] muestra un mensaje de estado en la Ventana de salida de una vez completada cada tarea.  Si no se puede completar una tarea, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] muestra un mensaje de error en la ventana Lista de errores.  
  
##  <a name="Features"></a> Características de proyecto de SharePoint  
 Una característica es una unidad portátil y modular de funcionalidad que simplifica la modificación de sitios mediante definiciones del sitio.  También es un paquete de elementos de [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] \(WSS\) que se puede activar para un ámbito concreto y que ayuda a los usuarios a lograr un objetivo o una tarea determinada.  Las plantillas se implementan como características.  
  
 Cuando se ejecuta un proyecto en modo de depuración, el proceso de implementación crea una carpeta en el directorio de la *característica* en %COMMONPROGRAMFILES%\\Microsoft Shared\\web server extensions\\14\\TEMPLATE\\FEATURES.  Los nombres de las características tienen el formato *project name*\_Feature*x*, como TestProject\_Feature1.  
  
 La carpeta de la solución en el directorio de características contiene un archivo de *definición de característica* y un archivo de *definición de flujo de trabajo*.  El archivo de definición de la característica \(feature.xml\) describe los archivos de la característica del proyecto.El archivo de definición del proyecto \(Elements.xml\) describe la plantilla de proyecto.  Elements.xml se encuentra en el **Explorador de soluciones**, pero Feature.xml se genera cuando se crea el paquete de solución.  Para obtener más información sobre estos archivos, vea [Plantillas de proyecto y de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
##  <a name="Workflow"></a> Depurar flujos de trabajo  
 Cuando se depuran proyectos de flujo de trabajo, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega la plantilla \(en función de su tipo\) de flujo de trabajo a una biblioteca o a una lista.  A continuación, puede iniciar la plantilla de flujo de trabajo manualmente o agregando o actualizando un elemento.  Después puede utilizar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para depurar el flujo de trabajo.  
  
> [!NOTE]  
>  Si agrega referencias a otros ensamblados, asegúrese de que esos ensamblados se instalan en la caché global de ensamblados \([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]\).  De lo contrario, se producirá un error en la solución de flujo de trabajo.  Para obtener más información sobre cómo instalar ensamblados, vea [Iniciar manualmente un flujo de trabajo en un documento o elemento](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
 Sin embargo, el proceso de implementación no inicia el flujo de trabajo.  Debe iniciar el flujo de trabajo desde el sitio web de SharePoint.  También puede iniciar el flujo de trabajo utilizando una aplicación cliente como Microsoft Office Word 2010 o bien mediante código de servidor independiente.  Utilice uno de los enfoques especificado en el **Asistente para personalización de SharePoint**.  
  
 Por ejemplo, si especificó que se puede iniciar el flujo de trabajo manualmente, inicie directamente el flujo de trabajo desde el elemento de la biblioteca o lista.  Para obtener más información sobre cómo iniciar un flujo de trabajo manualmente, vea [Iniciar manualmente un flujo de trabajo en un documento o elemento](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
##  <a name="FeatureEvents"></a> Depurar receptores de eventos de características  
 De forma predeterminada, al ejecutar la aplicación de SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sus características se activan automáticamente en el servidor de SharePoint.  Sin embargo, esto produce problemas al depurar los receptores de eventos de las características, porque cuando [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] activa una característica, se ejecuta en un proceso diferente que el depurador.  Esto significa que alguna funcionalidad de depuración, como los puntos de interrupción, no funcionará correctamente.  
  
 Para deshabilitar la activación automática de la característica en SharePoint y permitir la depuración correcta de los Receptores de eventos de características, establezca el valor de la propiedad **Active Deployment Configuration** del proyecto en **No Activation** antes de depurar.  A continuación, una vez que empiece a depurar su aplicación de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], active manualmente la característica en SharePoint.  Para activar la característica, abra el menú **Acciones del sitio** en SharePoint, elija **Configuración del sitio**, elija el vínculo **Administrar las características del sitio** y, a continuación, elija el botón **Activar** situado junto a la característica para continuar la depuración de forma habitual.  
  
##  <a name="EnhancedDebug"></a> Habilitar la información de depuración mejorada  
 Debido a las interacciones a veces complejas entre el proceso de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(devenv.exe\), el proceso host de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(vssphost4.exe\), SharePoint y la capa de WCF, los errores de diagnóstico que se producen durante la compilación, implementación, etc., pueden suponer un auténtico reto.  Para ayudarle a resolverlos, puede habilitar la información de depuración mejorada.  Para ello, entre en la clave del Registro siguiente en el Registro de Windows:  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\11.0\\SharePointTools\]  
  
 Si ya no existe el valor "EnableDiagnostics" **REG\_DWORD**, créelo manualmente.  Establezca el valor “EnableDiagnostics” en "1."  
  
 Si se establece su valor en 1, la información del seguimiento de la pila aparecerá en la **ventana de salida** cuando se produzcan errores en el sistema de proyectos durante la ejecución en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Para deshabilitar la información de depuración mejorada, establezca de nuevo el valor de EnableDiagnostics en 0, o elimine el valor.  
  
 Para obtener más información sobre otras claves del Registro de SharePoint, vea [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [Solucionar problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
  