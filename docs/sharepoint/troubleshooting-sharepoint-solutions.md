---
title: Solución de problemas de las soluciones de SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9f029cad2b0c8cb215a054502de5bc693cce5df5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928963"
---
# <a name="troubleshoot-sharepoint-solutions"></a>Solucionar problemas de soluciones de SharePoint
  Los siguientes problemas o alertas pueden producirse al depurar las soluciones de SharePoint mediante el depurador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información, consulte [depurar soluciones de flujo de trabajo de SharePoint 2007](http://msdn.microsoft.com/en-us/3a5392f3-66f3-48be-956e-02de23fa6247).
  
## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Restricciones de token en elementos web visuales en espacio aislado
 Los elementos web visuales en soluciones en espacio aislado no pueden procesar tokens estándar, como $SPUrl, que admite el runtime de SharePoint. Como resultado, la dirección URL no se soluciona y no se puede obtener una vista previa del contenido en la vista Diseño del diseñador del elemento web visual, si se hace referencia directamente en un elemento script, como en el ejemplo siguiente:  
  
```xml  
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>  
```  
  
 Para solucionar esta limitación y resolver el token, haga referencia al elemento script utilizando literales:  
  
```xml  
<asp:literal ID="Literal1" runat="server" Text="<script src='" />  
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />  
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />  
```  
  
## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Restricciones de caracteres en nombres de proyectos y elementos de proyecto
 Los nombres de proyecto y de elemento de proyecto solo pueden contener caracteres válidos para una ruta de distribución de SharePoint 2010. No se permite ningún otro carácter.  
  
### <a name="error-message"></a>Mensaje de error
 Mensaje de error "Caracteres no válidos".  
  
### <a name="resolution"></a>Resolución  
 En los nombres de los proyectos de SharePoint y de elementos de proyecto, solo se deben usar los siguientes caracteres:  
  
- Caracteres ASCII alfanuméricos  
  
- Espacio  
  
- Punto (.)  
  
- Coma (,)  
  
- Subrayado (_)  
  
- Guión (-)  
  
- Barra diagonal inversa (\\)  
  
  Cuando se empaqueta un proyecto, una regla de validación comprueba que la propiedad de ruta de acceso de implementación de cada archivo que se está implementando contiene solo estos caracteres válidos.  
  
## <a name="errors-when-creating-custom-fields"></a>Errores al crear campos personalizados
 En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], los campos personalizados se definen en XML. Se pueden producir errores si un campo no está definido o no se hace referencia a él con un formato concreto.  
  
### <a name="error-message"></a>Mensaje de error
 Mensaje de error "Caracteres no válidos" durante el empaquetado.  
  
### <a name="resolution"></a>Resolución  
 El identificador de una definición de campo debe ser un GUID entre llaves, como se muestra en el ejemplo siguiente:  
  
```xml  
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Type="Note"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Group="A Custom Group">  
</Field>.  
```  
  
 Como se muestra en el ejemplo siguiente, se debe definir una referencia de campo en un tipo de contenido con el formato de elemento vacío (\<FieldRef / >), no mediante el uso de elementos de inicio y fin (\<FieldRef >\</FieldRef >):  
  
```xml  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 Si el origen XML del campo es incorrecto o no es un archivo XML válido, o presenta algún otro problema, aparece un error que indica que no se puede analizar el archivo.  
  
## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Nuevas definiciones de sitio distintos del inglés no aparecen en la página de creación de sitio después de la implementación
 Después de crear e implementar una definición de sitio mediante el uso de una versión distinta del inglés de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (es decir, una versión con una configuración regional [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] distinto del 1033), el **personalizaciones de SharePoint** pestaña no aparecerá en el **Selección de plantilla** cuadro y la nueva plantilla de sitio no aparece en el **nuevo sitio de SharePoint** página.  
  
### <a name="error-message"></a>Mensaje de error
 Ninguno.  
  
### <a name="resolution"></a>Resolución  
 Este problema se produce debido a un valor incorrecto en el **ruta** como propiedad de la configuración de definición de sitio webtemp archivo *webtemp_SiteDefinitionProject1.xml*. En el **ruta** propiedad para el archivo webtemp, situado bajo el **ubicación de implementación**, cambie 1033 por la configuración regional adecuada [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Por ejemplo, para usar una configuración regional para japonés cambie el valor a 1041. Para obtener más información, consulte [Locale IDs Assigned by Microsoft](http://go.microsoft.com/fwlink/?LinkID=165561) en el sitio Web de MSDN.  
  
## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Aparece un error al implementar un proyecto de flujo de trabajo en un sistema limpio
 Este problema se produce si se implementa un proyecto de flujo de trabajo en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], en un sistema limpio. Un sistema limpio es un equipo que tiene una instalación nueva de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y SharePoint, pero no tiene ningún proyecto de flujo de trabajo implementado.  
  
### <a name="error-message"></a>Mensaje de error
 No se encuentra la lista de SharePoint: Historial del flujo de trabajo.  
  
### <a name="resolution"></a>Resolución  
 Este error se produce porque falta una lista del historial del flujo de trabajo. Dado que el entorno de desarrollo es un sistema limpio, no se implementa ningún flujo de trabajo y la lista del historial de flujo de trabajo no existe todavía. Para resolver este problema, vuelva a abrir el asistente de flujo de trabajo, lo que hará que se cree la lista del historial de flujo de trabajo.  
  
##### <a name="to-reenter-the-workflow-wizard"></a>Para volver a entrar en el asistente de flujo de trabajo  
  
1.  En **el Explorador de soluciones**, elija el nodo de flujo de trabajo.  
  
2.  En el **propiedades** ventana, elija el botón de puntos suspensivos (...) en cualquier propiedad que tenga un botón de puntos suspensivos.  
  
## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>Usuario debe actualizar la página de aplicación en el explorador mientras se depura para ver la imagen actualizada
 Si está depurando una solución de SharePoint que contiene una página de aplicación con un control en el que se muestra una imagen, como un control de imagen [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)], es necesario actualizar la página en el explorador para mostrar los cambios que se realizan en la imagen.  
  
## <a name="error-the-site-location-is-not-valid"></a>Error: La ubicación del sitio no es válida
 Este problema puede producirse si no se instala [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]. También puede ocurrir si no tiene acceso de administrador al sitio Web de SharePoint que se especifica en el **Asistente de personalización de SharePoint**.  
  
### <a name="error-message"></a>Mensaje de error
  
-   La ubicación del sitio de SharePoint no es válida.  
  
### <a name="resolution"></a>Resolución  
  
-   Instale [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
-   Asegúrese de que tiene acceso de administrador al sitio web de SharePoint. Para obtener más información, consulte el [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] artículo en línea [asignar o quitar administradores de aplicaciones de servicio en SharePoint Server](https://docs.microsoft.com/en-us/sharepoint/administration/assign-or-remove-administrators-of-service-applications).  
  
## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>Evento web de eliminación de sitio no aparece en el proyecto de receptor de eventos
 Cuando crea un proyecto de receptor de eventos y selecciona ciertos eventos web como "Se va a eliminar un sitio", el evento nunca se produce.  
  
### <a name="error-message"></a>Mensaje de error
 Ninguno.  
  
### <a name="resolution"></a>Resolución  
 Este problema se produce porque el ámbito de característica debe ser "Sitio" para poder administrar eventos del nivel de sitio, pero el ámbito de característica predeterminado en los proyectos de receptor de eventos es "Web". Los eventos web afectados son:  
  
- Se va a eliminar un sitio (WebDeleting)  
  
- Se eliminó un sitio (WebDeleted)  
  
- Se va a mover un sitio (WebMoving)  
  
- Se movió un sitio (WebMoved)  
  
  Para corregir el problema, cambie el ámbito de característica del receptor de eventos tal y como se indica a continuación.  
  
##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Para cambiar el ámbito de característica del receptor de eventos  
  
1.  En **el Explorador de soluciones**, abra el receptor de eventos *.feature* de archivos en el **característica Diseñador** doble clic en el archivo o abriendo su menú contextual y, a continuación, elegir **abierto**.  
  
2.  Elija la flecha situada junto a **ámbito**y, a continuación, elija **sitio** en la lista que aparece.  
  
## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>Error de implementación aparece después de cambia el nombre de un identificador en un proyecto de modelo de conectividad de datos empresariales
 Este problema se produce si cambia el nombre del identificador de una entidad de un modelo de conectividad a datos profesionales (BDC) y, a continuación, intenta implementar la solución.  
  
### <a name="error-messages"></a>Mensajes de error
  
-   \<*nombre del modelo*> tiene los siguientes errores de activación de tipo de contenido externo...  
  
-   El IMetadataObject denominado '\<*nombre del modelo*>' tiene un valor en el campo 'nombre' que está duplicado...  
  
### <a name="resolution"></a>Resolución  
 Para resolver este problema, elimine el modelo manualmente y, a continuación, implemente de nuevo la solución.  Puede eliminar el modelo utilizando cualquiera de las siguientes herramientas:  
  
-   Administración central de SharePoint 2010. Para obtener más información, consulte [BDC Model Management](http://go.microsoft.com/fwlink/?LinkID=181472) en el sitio Web de Microsoft TechNet.  
  
-   Windows PowerShell. Puede eliminar el modelo, escriba este comando en el símbolo del sistema: **Remove-SPBusinessDataCatalogModel**. Para obtener más información, consulte [cmdlets generales (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkID=182375) en el sitio Web de Microsoft TechNet.  
  
## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Aparece un error al intentar ver un elemento web visual en SharePoint
 Este problema se produce cuando el **ruta** propiedad del control de usuario no comienza con la cadena "CONTROLTEMPLATES\\".  
  
### <a name="error-messages"></a>Mensajes de error
  
-   El archivo ' / _controltemplates /*\<nombre del proyecto >*/*\<nombre del elemento Web >*/*\<control de usuario nombre >* ascx ' no existe.  
  
-   Error del servidor en la aplicación '/'.  
  
### <a name="resolution"></a>Resolución  
  
##### <a name="to-resolve-this-issue"></a>Para resolver este problema  
  
1.  En **el Explorador de soluciones**, elija el archivo de control de usuario, cuya extensión de nombre de archivo es *.ascx*.  
  
2.  En la barra de menús, elija **vista** > **ventana propiedades**.  
  
3.  En el **propiedades** ventana, expanda el **ubicación de implementación** nodo.  
  
4.  Asegúrese de que el valor de la **ruta** propiedad comienza con la cadena "CONTROLTEMPLATES\\".  
  
## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Error aparece cuando se ejecuta un flujo de trabajo reutilizable importado que contiene un campo de formulario de tareas
 Este problema se produce si importa un flujo de trabajo que contiene un formulario de tareas que incluye un campo y, a continuación, ejecuta el nuevo flujo de trabajo en el mismo sistema del que lo importó.  
  
### <a name="error-message"></a>Mensaje de error
 Se ha producido un error en el paso de implementación "Activar características": el campo con el Id. [*Guid*] definido en la característica [*Guid*] se encontró en la colección de sitios actual o en un subsitio.  
  
### <a name="resolution"></a>Resolución  
 Este error es el resultado de colisiones de identificador de campo que se producen porque el proyecto de flujo de trabajo reutilizable de importación en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no cambia los identificadores de campo de formulario de tareas. Si implementa un flujo de trabajo importado en el mismo servidor que contiene el flujo de trabajo original, se producen colisiones de identificador de campo.  
  
 Para resolver este problema, use la característica Buscar y reemplazar para cambiar el valor del atributo id. de campo en todos los archivos de flujo de trabajo importados.  
  
## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Aparece un error al importa un nuevo nombre se ejecuta la instancia de lista
 Este problema se produce si cambia el nombre de una instancia de lista importada y, a continuación, la ejecuta en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
### <a name="error-message"></a>Mensaje de error
 Error de compilación: se ha producido un Error en el paso de implementación "Activar características": el archivo Template\Features\\[*Importar proyecto*<em>característica</em>*nombre*] \Files\Lists \\[*antiguo*<em>nombre de la lista</em>] \Schema.xml no existe.  
  
### <a name="resolution"></a>Resolución  
 Al importar una instancia de lista, se agrega un atributo denominado CustomSchema al archivo Elements.xml de la instancia de lista. Elements.xml incluye la ruta de acceso de un archivo schema.xml personalizado para la instancia de lista. Al cambiar el nombre de la instancia de lista en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cambia la ruta de acceso de implementación para el archivo schema.xml personalizado, pero el valor de ruta de acceso del atributo CustomSchema no se actualiza. Como resultado, no se encuentra la instancia de lista la *schema.xml* archivo en la ruta de acceso anterior especificada por el atributo CustomSchema cuando se activa la característica.  
  
 Para resolver este problema, actualice la ruta de acceso de la ubicación de implementación de la *schema.xml* archivo en el atributo CustomSchema.  
  
## <a name="sharepoint-debugging-session-terminated-by-iis"></a>IIS finalizada la sesión de depuración de SharePoint
 Este problema se produce si establece un punto de interrupción un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] solución de SharePoint, elija el **F5** clave para ejecutarlo y, a continuación, permanecer en un punto de interrupción durante más de 90 segundos.  
  
### <a name="error-message"></a>Mensaje de error
 Internet Information Services (IIS) ha finalizado el proceso del servidor web que se estaba depurando. Para evitar este problema, puede configurar los valores del comando ping del grupo de aplicaciones en IIS. Vea la Ayuda para obtener más información.  
  
### <a name="resolution"></a>Resolución  
 De forma predeterminada, el grupo de aplicaciones de IIS espera 90 segundos a que una aplicación responda antes de cerrarla. Este proceso se conoce como "hacer ping" a la aplicación. Para resolver este problema, puede aumentar el tiempo de espera o deshabilitar el ping de la aplicación por completo.  
  
##### <a name="to-access-the-iis-app-pool-settings"></a>Para obtener acceso a los valores de grupo de aplicación de IIS  
  
1.  Abra el Administrador de IIS.  
  
2.  En el **conexiones** panel, expanda el nodo del servidor de SharePoint y, a continuación, elija el **grupos de aplicaciones** nodo.  
  
3.  En el **grupos de aplicaciones** página, elija el grupo de aplicaciones de SharePoint (normalmente "SharePoint - 80") y, a continuación, en el **acciones** panel, elija el **configuración avanzada** vínculo.  
  
4.  Para aumentar el tiempo de espera antes de tiempo de espera IIS, cambie el valor de **tiempo máximo de respuesta de Ping (segundos)** en un valor que es mayor que 90 segundos.  
  
5.  Para deshabilitar el ping en IIS, establezca **Ping habilitado** a **False**.  
  
## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Retracción automática deja la instancia de lista huérfanos en SharePoint
 Este problema se produce si realiza los siguientes pasos.  
  
1.  Crea una definición de lista que contiene una instancia de lista en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Elija la **F5** clave para ejecutar la solución.  
  
3.  Detiene la depuración o cierra el sitio de SharePoint.  
  
4.  Vuelve a abrir el sitio de SharePoint y abre la instancia de lista.  
  
### <a name="error-message"></a>Mensaje de error
 Error del servidor en la aplicación '/'.  
  
### <a name="resolution"></a>Resolución  
 Esto ocurre porque después de cerrar una sesión de depuración de una solución de SharePoint, la característica de retracción automática retrae la solución. La retractación elimina la definición de lista de SharePoint pero no elimina la instancia de lista. La instancia de lista requiere la definición de lista subyacente.  
  
 Para resolver este problema, implemente la solución, en la barra de menús, elija **compilar** > **implementar**. (No depure la solución eligiendo la **F5** clave.) A continuación, elimine la instancia de lista en SharePoint.  
  
## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>Solución de SharePoint original se reemplaza por una versión exportada
 Si exporta una solución de SharePoint, importa la solución a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y, a continuación, vuelve a implementar la solución en el mismo sitio del que la exportó, se reemplaza la solución de SharePoint original. Este problema no se produce si implementa la solución en un servidor que no tiene activada la solución original.  
  
### <a name="error-message"></a>Mensaje de error
 Ninguno.  
  
### <a name="resolution"></a>Resolución  
 Para evitar sobrescribir una solución en el sitio del que se exportó, cambie los GUID de SolutionID y los identificadores de todas las características importadas en el proyecto de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## <a name="error-appears-when-debugging-starts"></a>Aparece un error al iniciar la depuración
 Al empezar a depurar una solución de SharePoint en Visual Studio, se recibe un error que indica que Visual Studio no pudo cargar el archivo de configuración Web.config porque la clave especificada no se encontró en el diccionario.  
  
### <a name="error-message"></a>Mensaje de error
 No se puede cargar el archivo de configuración Web.config. Compruebe que el archivo no contiene elementos XML incorrectos e inténtelo de nuevo. Se produjo el siguiente error: La clave especificada no se encontró en el diccionario.  
  
### <a name="resolution"></a>Resolución  
 Para resolver este problema, asegúrese de que el valor de propiedad URL del sitio del proyecto de SharePoint en Visual Studio coincide con la dirección URL que está asignada a la zona predeterminada para las asignaciones de acceso alternativas de la aplicación web. No se resuelve el error si se usa otra zona, como la intranet, para la dirección URL. La dirección URL del sitio del proyecto y la dirección URL de la zona predeterminada deben coincidir. Para obtener acceso a las asignaciones de acceso alternativas, abra la utilidad de Administración Central de SharePoint 2010, elija el **Application Management** vínculo y, a continuación, en **aplicaciones Web**, elija el  **Configurar asignaciones de acceso alternativas** vínculo. Para obtener más información, consulte [crear zonas para las aplicaciones Web](http://go.microsoft.com/fwlink/?LinkId=192274).  
  
## <a name="see-also"></a>Vea también
 [Solucionar problemas de implementación y empaquetado de SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [Compilar y depurar soluciones de SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Depurar en Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
  
  
