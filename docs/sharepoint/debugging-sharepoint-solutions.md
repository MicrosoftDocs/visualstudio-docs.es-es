---
title: Depurar soluciones de SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6f53ca7f1a5e449d47a30a32967072f7220c159a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903158"
---
# <a name="debug-sharepoint-solutions"></a>Depurar soluciones de SharePoint
  Puede depurar las soluciones de SharePoint utilizando el depurador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Al iniciar la depuración, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] implementa los archivos de proyecto en el servidor de SharePoint y, a continuación, se abre una instancia del sitio de SharePoint en el explorador Web. En las secciones siguientes se explica cómo depurar aplicaciones de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [Habilitar la depuración](#EnableDebug)  
  
-   [Depuración con F5 y proceso de implementación](#Deployment)  
  
-   [Características de proyecto de SharePoint](#Features)  
  
-   [Depuración de flujos de trabajo](#Workflow)  
  
-   [Depurar receptores de eventos de característica](#FeatureEvents)  
  
-   [Habilitar información de depuración mejorada](#EnhancedDebug)  
  
## <a name="enable-debugging"></a>Habilitar depuración
 Cuando se depura por primera vez una solución de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], un cuadro de diálogo advierte de que el archivo web.config no está configurado para habilitar la depuración. (Se crea el archivo web.config al instalar el servidor de SharePoint. Para obtener más información, consulte [trabajar con archivos Web.config](http://go.microsoft.com/fwlink/?LinkID=149266).) El cuadro de diálogo da la opción de ejecutar el proyecto sin depurar o modificar el archivo web.config para habilitar la depuración. Si elige la primera opción, el proyecto se ejecuta normalmente. Si elige la segunda opción, el archivo web.config se configura para:  
  
- Activar la pila de llamadas (`CallStack="true"`)  
  
- Deshabilitar los errores personalizados en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="Off" />`)  
  
- Habilitar la depuración de compilación (`<compilation debug="true">`)  
  
  A continuación se puede ver el archivo web.config resultante:  
  
```xml  
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
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
  
 Para revertir los cambios y deshabilitar la depuración, cambie la siguiente [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] en el archivo web.config:  
  
-   Desactivar la pila de llamadas (`CallStack="false"`)  
  
-   Habilitar errores personalizados en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="On" />`)  
  
-   Deshabilitar la depuración de compilación (`<compilation debug="false">`)  
  
## <a name="f5-debug-and-deployment-process"></a>Proceso de depuración e implementación de F5
 Cuando se ejecuta un proyecto de SharePoint en modo de depuración, el proceso de implementación de SharePoint realiza las tareas siguientes:  
  
1. Ejecuta los comandos anteriores a la implementación personalizables.  
  
2. Crea un archivo (.wsp) de solución web mediante comandos de [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)]. El archivo .wsp incluye todos los archivos y características necesarios. Para obtener más información, consulte [información general sobre soluciones](http://go.microsoft.com/fwlink/?LinkID=128154).  
  
3. Si la solución de SharePoint es una solución de granja, recicla el grupo de aplicaciones de [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] para la [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] del sitio especificado. Este paso libera los archivos bloqueados por el proceso de trabajo de [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)].  
  
4. Si ya existe una versión anterior del paquete, la retira de las características y los archivos del archivo .wsp. Este paso desactiva las características, desinstala el paquete de la solución y, a continuación, lo elimina del servidor de SharePoint.  
  
5. Instala la versión actual de las características y archivos en el archivo .wsp. Este paso agrega e instala la solución en el servidor de SharePoint.  
  
6. Para los flujos de trabajo, instala el ensamblado del flujo de trabajo. Puede cambiar su ubicación mediante el *ubicación del ensamblado* propiedad.  
  
7. Activa la característica del proyecto en SharePoint si el ámbito es Sitio o Web. No se activan las características de los ámbitos de aplicación web y granja de servidores.  
  
8. Para los flujos de trabajo, asocia el flujo de trabajo con la biblioteca de SharePoint, lista o un sitio que seleccionó en el **Asistente de personalización de SharePoint**.  
  
   > [!NOTE]  
   >  Esta asociación solo se produce si seleccionó **automáticamente la asociación de flujo de trabajo** en el asistente.  
  
9. Ejecuta los comandos posteriores a la implementación personalizables.  
  
10. Adjunta el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] del depurador para el [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] proceso (*w3wp.exe*). Si el tipo de proyecto permite cambiar el *solución en espacio aislado* propiedad y su valor se establece en **true**, a continuación, el depurador se asocia a un proceso diferente (*SPUCWorkerProcess.exe*). Para obtener más información, consulte [consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
11. Inicia el depurador de JavaScript si la solución de SharePoint es una solución de granja.  
  
12. Muestra la biblioteca, lista o página de sitio adecuada en el explorador web.  
  
    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] muestra un mensaje de estado en la Ventana de salida de una vez completada cada tarea. Si no se puede completar una tarea, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] muestra un mensaje de error en la ventana Lista de errores.  
  
## <a name="sharepoint-project-features"></a>Características de proyecto de SharePoint
 Una característica es una unidad portátil y modular de funcionalidad que simplifica la modificación de sitios mediante definiciones del sitio. También es un paquete de [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] los elementos (WSS) que se puede activar para un ámbito concreto y que ayuda a los usuarios a lograr un objetivo determinado o una tarea. Las plantillas se implementan como características.  
  
 Cuando se ejecuta un proyecto en modo de depuración, el proceso de implementación crea una carpeta en el *característica* directorio en *%COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES*. Los nombres de función tienen el formato *nombre del proyecto*_Feature*x*, como TestProject_Feature1.  
  
 Carpeta de la solución en el directorio de características contiene un *definición de la característica* archivo y un *definición de flujo de trabajo* archivo. El archivo de definición de característica (Feature.xml) describe los archivos en el archivo de definición de proyecto del proyecto WAS (*Elements.xml*) describe la plantilla de proyecto. *Elements.XML* puede encontrarse en **el Explorador de soluciones**, pero Feature.xml se genera cuando se crea el paquete de solución. Para obtener más información acerca de estos archivos, consulte [SharePoint plantillas de elemento de proyecto y](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
## <a name="debug-workflows"></a>Flujos de trabajo de depuración
 Cuando se depuran proyectos de flujo de trabajo, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega la plantilla (en función de su tipo) de flujo de trabajo a una biblioteca o a una lista. A continuación, puede iniciar la plantilla de flujo de trabajo manualmente o agregando o actualizando un elemento. Después puede utilizar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para depurar el flujo de trabajo.  
  
> [!NOTE]
>  Si agrega referencias a otros ensamblados, asegúrese de que esos ensamblados se instalan en la caché global de ensamblados ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). De lo contrario, se producirá un error en la solución de flujo de trabajo. Para obtener información sobre cómo instalar ensamblados, vea [iniciar manualmente un flujo de trabajo en un documento o elemento](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).  
  
 Sin embargo, el proceso de implementación no inicia el flujo de trabajo. Debe iniciar el flujo de trabajo desde el sitio web de SharePoint. También puede iniciar el flujo de trabajo utilizando una aplicación cliente como Microsoft Office Word 2010 o bien mediante código de servidor independiente. Utilice uno de los enfoques especificado en el **Asistente de personalización de SharePoint**.  
  
 Por ejemplo, si especificó que se puede iniciar el flujo de trabajo manualmente, inicie directamente el flujo de trabajo desde el elemento de la biblioteca o lista. Para obtener más información sobre cómo iniciar un flujo de trabajo manualmente, consulte [iniciar manualmente un flujo de trabajo en un elemento de documento](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).  
  
## <a name="debug-feature-event-receivers"></a>Depurar receptores de eventos de característica
 De forma predeterminada, al ejecutar la aplicación de SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sus características se activan automáticamente en el servidor de SharePoint. Sin embargo, esto produce problemas al depurar receptores de eventos de característica, ya que cuando se activa una característica por [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], se ejecuta en un proceso diferente que el depurador. Esto significa que alguna funcionalidad de depuración, como los puntos de interrupción, no funcionará correctamente.  
  
 Para deshabilitar la activación automática de la característica en SharePoint y permitir la depuración correcta de receptores de eventos de característica, establezca el valor del proyecto **Active Deployment Configuration** propiedad **sin activación** antes de depurar. A continuación, una vez que empiece a depurar su aplicación de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], active manualmente la característica en SharePoint. Para activar la característica, abra el **acciones del sitio** en SharePoint, elija **configuración del sitio**, elija el **administrar las características del sitio** vincular y, a continuación, elija el **Activar** botón situado junto a la característica para continuar con la depuración con normalidad.  
  
## <a name="enable-enhanced-debug-information"></a>Habilitar información de depuración mejorada
 Debido a las interacciones a veces complejas entre el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proceso (devenv.exe), el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proceso de host de SharePoint (*vssphost4.exe*), SharePoint y la capa de WCF, diagnóstico de errores que se producen mientras creación, implementación etc. pueden ser un desafío. Para ayudarle a resolverlos, puede habilitar la información de depuración mejorada. Para ello, entre en la clave del Registro siguiente en el Registro de Windows:  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**  
  
 Si el "EnableDiagnostics" **REG_DWORD** valor ya no existe, créelo manualmente. Establezca el valor "EnableDiagnostics" en "1".  
  
 Establecer este valor de clave en 1 pila causas información de seguimiento en aparecer en el **salida** ventana cada vez que se producen errores de sistema de proyecto mientras se ejecutan [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para deshabilitar la información de depuración mejorada, establezca de nuevo el valor de EnableDiagnostics en 0, o elimine el valor.  
  
 Para obtener más información sobre otras claves del registro de SharePoint, vea [depurar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también
 [Solucionar problemas de soluciones de SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
