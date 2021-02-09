---
title: Solucionar problemas de soluciones de SharePoint | Microsoft Docs
description: Vea qué problemas o alertas pueden producirse al depurar soluciones de SharePoint mediante el depurador de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/22/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c6b0e031e96d2543ae0bb109f243824125f431a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892299"
---
# <a name="troubleshoot-sharepoint-solutions"></a>Solucionar problemas de soluciones de SharePoint
  Los siguientes problemas o alertas pueden producirse al depurar las soluciones de SharePoint mediante el depurador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información, vea [depurar soluciones de flujo de trabajo de SharePoint 2007](/previous-versions/bb386166(v=vs.100)).

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Restricciones de token en elementos Web visuales en espacio aislado
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
 Mensaje de error "caracteres no válidos".

### <a name="resolution"></a>Solución
 En los nombres de los proyectos de SharePoint y de elementos de proyecto, solo se deben usar los siguientes caracteres:

- Caracteres ASCII alfanuméricos

- Space

- Punto (.)

- Coma (,)

- Subrayado (_)

- Guión (-)

- Barra diagonal inversa (\\)

  Cuando se empaqueta un proyecto, una regla de validación comprueba que la propiedad de ruta de acceso de implementación de cada archivo que se está implementando contiene solo estos caracteres válidos.

## <a name="errors-when-creating-custom-fields"></a>Errores al crear campos personalizados
 En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], los campos personalizados se definen en XML. Se pueden producir errores si un campo no está definido o no se hace referencia a él con un formato concreto.

### <a name="error-message"></a>Mensaje de error
 Mensaje de error "caracteres no válidos" en el tiempo de empaquetado.

### <a name="resolution"></a>Solución
 El identificador de una definición de campo debe ser un GUID entre llaves, como se muestra en el ejemplo siguiente:

```xml
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Type="Note"
    Name="PatientName"
    DisplayName="Patient Name"
    Group="A Custom Group">
</Field>.
```

 Como se muestra en el ejemplo siguiente, una referencia de campo en un tipo de contenido debe definirse con el formato de elemento vacío ( \<FieldRef /> ), no mediante los elementos de inicio y fin ( \<FieldRef> \</FieldRef> ):

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 Si el origen XML del campo es incorrecto o no es un archivo XML válido, o presenta algún otro problema, aparece un error que indica que no se puede analizar el archivo.

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Las nuevas definiciones de sitios que no están en inglés no aparecen en la página de creación de sitios después de la implementación
 Después de crear e implementar una definición de sitio con una versión que no esté en Inglés de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (es decir, una versión con una configuración regional que no [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] sea 1033), la pestaña **personalizaciones de SharePoint** no aparece en el cuadro de **selección de plantilla** y la plantilla de sitio nuevo no aparece en la página **nuevo sitio de SharePoint** .

### <a name="error-message"></a>Mensaje de error
 Ninguno.

### <a name="resolution"></a>Solución
 Este problema se produce debido a un valor incorrecto en la propiedad **path** del archivo de configuración de la definición del sitio WebTemp, como *webtemp_SiteDefinitionProject1.xml*. En la propiedad **ruta de acceso** del archivo WebTemp, situado en la ubicación de **implementación**, cambie 1033 a la configuración regional adecuada [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Por ejemplo, para usar la configuración regional del japonés, cambie el valor a 1041. Para obtener más información, vea [Id. de configuración regional asignados por Microsoft](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c).

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Aparece un error cuando se implementa un proyecto de flujo de trabajo en un sistema limpio
 Este problema se produce si se implementa un proyecto de flujo de trabajo en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], en un sistema limpio. Un sistema limpio es un equipo que tiene una instalación nueva de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y SharePoint, pero no tiene ningún proyecto de flujo de trabajo implementado.

### <a name="error-message"></a>Mensaje de error
 No se encuentra la lista de SharePoint: Historial del flujo de trabajo.

### <a name="resolution"></a>Solución
 Este error se produce porque falta una lista del historial del flujo de trabajo. Dado que el entorno de desarrollo es un sistema limpio, no se implementa ningún flujo de trabajo y la lista del historial de flujo de trabajo no existe todavía. Para resolver este problema, vuelva a abrir el asistente de flujo de trabajo, lo que hará que se cree la lista del historial de flujo de trabajo.

##### <a name="to-reenter-the-workflow-wizard"></a>Para volver a entrar en el asistente de flujo de trabajo

1. En **Explorador de soluciones**, elija el nodo flujo de trabajo.

2. En la ventana **propiedades** , elija el botón de puntos suspensivos (...) en cualquier propiedad que tenga un botón de puntos suspensivos.

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>El usuario debe actualizar la página de la aplicación en el explorador durante la depuración para ver la imagen actualizada
 Si está depurando una solución de SharePoint que contiene una página de aplicación con un control en el que se muestra una imagen, como un control de imagen [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)], es necesario actualizar la página en el explorador para mostrar los cambios que se realizan en la imagen.

## <a name="error-the-site-location-is-not-valid"></a>Error: la ubicación del sitio no es válida
 Este problema puede producirse si no se instala [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]. También puede producirse si no tiene acceso de administrador al sitio web de SharePoint que se especifica en el **Asistente para la personalización de SharePoint**.

### <a name="error-message"></a>Mensaje de error

- La ubicación del sitio de SharePoint no es válida.

### <a name="resolution"></a>Solución

- Instalar [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].

- Asegúrese de que tiene acceso de administrador al sitio web de SharePoint. Para obtener más información, vea el [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] artículo en línea [asignación o eliminación de administradores de aplicaciones de servicio en SharePoint Server](/sharepoint/administration/assign-or-remove-administrators-of-service-applications).

## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>El evento web de eliminación de sitios no se produce en el proyecto de receptor de eventos
 Cuando crea un proyecto de receptor de eventos y selecciona ciertos eventos web como "Se va a eliminar un sitio", el evento nunca se produce.

### <a name="error-message"></a>Mensaje de error
 Ninguno.

### <a name="resolution"></a>Solución
 Este problema se produce porque el ámbito de característica debe ser "Sitio" para poder administrar eventos del nivel de sitio, pero el ámbito de característica predeterminado en los proyectos de receptor de eventos es "Web". Los eventos web afectados son:

- Se va a eliminar un sitio (WebDeleting)

- Se eliminó un sitio (WebDeleted)

- Se va a mover un sitio (WebMoving)

- Se movió un sitio (WebMoved)

  Para corregir el problema, cambie el ámbito de característica del receptor de eventos tal y como se indica a continuación.

##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Para cambiar el ámbito de característica del receptor de eventos

1. En **Explorador de soluciones**, abra el archivo *. Feature* del receptor de eventos en el **Diseñador de características** ; para ello, haga doble clic en el archivo o abra el menú contextual y, a continuación, elija **abrir**.

2. Elija la flecha situada junto a **ámbito** y, a continuación, elija **sitio** en la lista que aparece.

## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>El error de implementación aparece después de cambiar el nombre de un identificador en un proyecto de modelo de conectividad a datos profesionales
 Este problema se produce si cambia el nombre del identificador de una entidad de un modelo de conectividad a datos profesionales (BDC) y, a continuación, intenta implementar la solución.

### <a name="error-messages"></a>Mensajes de error

- \<*model name*> tiene los siguientes errores de activación de tipo de contenido externo...

- El IMetadataObject con el nombre ' \<*model name*> ' tiene un valor en el campo ' nombre ' que está duplicado...

### <a name="resolution"></a>Solución
 Para resolver este problema, elimine el modelo manualmente y, a continuación, implemente de nuevo la solución.  Puede eliminar el modelo utilizando cualquiera de las siguientes herramientas:

- Administración central de SharePoint 2010. Para obtener más información, vea [BDC administración de modelos](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)#delete-a-bdc-model) en el sitio web de Microsoft TechNet.

- Windows PowerShell. Puede eliminar el modelo escribiendo este comando en el símbolo del sistema: **Remove-SPBusinessDataCatalogModel**. Para obtener más información, vea [cmdlets generales (SharePoint Server 2010)](/powershell/module/sharepoint-server) en el sitio web de Microsoft TechNet.

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Aparece un error al intentar ver un elemento Web visual en SharePoint
 Este problema se produce cuando la propiedad **path** del control de usuario no comienza con la cadena "CONTROLTEMPLATES \\ ".

### <a name="error-messages"></a>Mensajes de error

- El archivo '/_CONTROLTEMPLATES/ *\<project name>* / *\<Web Part name>* / *\<user control name>* . ascx ' no existe.

- Error del servidor en la aplicación '/'

### <a name="resolution"></a>Solución

##### <a name="to-resolve-this-issue"></a>Para resolver este problema

1. En **Explorador de soluciones**, elija el archivo de control de usuario, cuya extensión de nombre de archivo es *. ascx*.

2. En la barra de menús, elija **Ver**  >  **ventana Propiedades**.

3. En la ventana **propiedades** , expanda el nodo **Ubicación de implementación** .

4. Asegúrese de que el valor de la propiedad **path** comienza con la cadena "CONTROLTEMPLATES \\ ".

## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Aparece un error cuando se ejecuta un flujo de trabajo reutilizable importado que contiene un campo de formulario de tareas.
 Este problema se produce si importa un flujo de trabajo que contiene un formulario de tareas que incluye un campo y, a continuación, ejecuta el nuevo flujo de trabajo en el mismo sistema del que lo importó.

### <a name="error-message"></a>Mensaje de error
 Error en el paso de implementación "activar características": el campo con el identificador [*GUID*] definido en la característica [*GUID*] se encontró en la colección de sitios actual o en un subsitio.

### <a name="resolution"></a>Solución
 Este error es el resultado de los conflictos de ID. de campo que se producen porque el proyecto importar flujo de trabajo reutilizable de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no cambia los identificadores de campo del formulario de tareas. Si implementa un flujo de trabajo importado en el mismo servidor que contiene el flujo de trabajo original, se producen colisiones de identificador de campo.

 Para resolver este problema, use la característica Buscar y reemplazar para cambiar el valor del atributo id. de campo en todos los archivos de flujo de trabajo importados.

## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Aparece un mensaje de error cuando se ejecuta una instancia de lista importada con nombre
 Este problema se produce si cambia el nombre de una instancia de lista importada y, a continuación, la ejecuta en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

### <a name="error-message"></a>Mensaje de error
 Error de compilación: error en el paso de implementación ' activar características ': el archivo Template\Features \\ [*Import Project*<em>Feature</em>*Name*] \Files\Lists \\ [*Old*<em>List Name</em>] \Schema.xml no existe.

### <a name="resolution"></a>Solución
 Al importar una instancia de lista, se agrega un atributo denominado CustomSchema al archivo Elements.xml de la instancia de lista. Elements.xml incluye la ruta de acceso de un archivo schema.xml personalizado para la instancia de lista. Al cambiar el nombre de la instancia de lista en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cambia la ruta de acceso de implementación para el archivo schema.xml personalizado, pero el valor de ruta de acceso del atributo CustomSchema no se actualiza. Como resultado, la instancia de lista no puede encontrar el archivo de *schema.xml* en la ruta de acceso anterior especificada por el atributo CustomSchema cuando se activa la característica.

 Para resolver este problema, actualice la ruta de acceso de la ubicación de implementación del archivo de *schema.xml* en el atributo CustomSchema.

## <a name="sharepoint-debugging-session-terminated-by-iis"></a>IIS finalizó la sesión de depuración de SharePoint
 Este problema se produce si establece un punto de interrupción en una [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] solución de SharePoint, elige la tecla **F5** para ejecutarlo y, a continuación, permanece en un punto de interrupción de más de 90 segundos.

### <a name="error-message"></a>Mensaje de error
 Internet Information Services (IIS) ha finalizado el proceso del servidor web que se estaba depurando. Para evitar este problema, puede configurar los valores del comando ping del grupo de aplicaciones en IIS. Vea la Ayuda para obtener más información.

### <a name="resolution"></a>Solución
 De forma predeterminada, el grupo de aplicaciones de IIS espera 90 segundos a que una aplicación responda antes de cerrarla. Este proceso se conoce como "hacer ping" a la aplicación. Para resolver este problema, puede aumentar el tiempo de espera o deshabilitar el ping de la aplicación por completo.

##### <a name="to-access-the-iis-app-pool-settings"></a>Para obtener acceso a los valores de grupo de aplicación de IIS

1. Abra Administrador de IIS.

2. En el panel **conexiones** , expanda el nodo servidor de SharePoint y, a continuación, elija el nodo **grupos de aplicaciones** .

3. En la página **grupos de aplicaciones** , elija el grupo de aplicaciones de SharePoint (normalmente "sharepoint-80") y, a continuación, en el panel **acciones** , elija el vínculo **Configuración avanzada** .

4. Para aumentar el tiempo de espera antes de que se agote el tiempo de espera de IIS, cambie el valor de **tiempo máximo de respuesta de ping (segundos)** a un valor superior a 90 segundos.

5. Para deshabilitar el ping de IIS, establezca **ping habilitado** en **false**.

## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>La retirada automática deja la instancia de lista huérfana en SharePoint
 Este problema se produce si realiza los siguientes pasos.

1. Crea una definición de lista que contiene una instancia de lista en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Elija la tecla **F5** para ejecutar la solución.

3. Detiene la depuración o cierra el sitio de SharePoint.

4. Vuelve a abrir el sitio de SharePoint y abre la instancia de lista.

### <a name="error-message"></a>Mensaje de error
 Error del servidor en la aplicación '/'

### <a name="resolution"></a>Solución
 Esto ocurre porque después de cerrar una sesión de depuración de una solución de SharePoint, la característica de retracción automática retrae la solución. La retractación elimina la definición de lista de SharePoint pero no elimina la instancia de lista. La instancia de lista requiere la definición de lista subyacente.

 Para resolver este problema, implemente la solución mediante, en la barra de menús, elija **compilar**  >  **implementar**. (No depure la solución eligiendo la tecla **F5** ). A continuación, elimine la instancia de la lista en SharePoint.

## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>La solución de SharePoint original se reemplaza por una versión exportada
 Si exporta una solución de SharePoint, importa la solución a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y, a continuación, vuelve a implementar la solución en el mismo sitio del que la exportó, se reemplaza la solución de SharePoint original. Este problema no se produce si implementa la solución en un servidor que no tiene activada la solución original.

### <a name="error-message"></a>Mensaje de error
 Ninguno.

### <a name="resolution"></a>Solución
 Para evitar sobrescribir una solución en el sitio del que se exportó, cambie los GUID de SolutionID y los identificadores de todas las características importadas en el proyecto de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

## <a name="error-appears-when-debugging-starts"></a>El error aparece cuando se inicia la depuración
 Al empezar a depurar una solución de SharePoint en Visual Studio, se recibe un error que indica que Visual Studio no pudo cargar el archivo de configuración Web.config porque la clave especificada no se encontró en el diccionario.

### <a name="error-message"></a>Mensaje de error
 No se puede cargar el archivo de configuración Web.config. Compruebe que el archivo no contiene elementos XML incorrectos e inténtelo de nuevo. Se produjo el siguiente error: La clave especificada no se encontró en el diccionario.

### <a name="resolution"></a>Solución
 Para resolver este problema, asegúrese de que el valor de propiedad URL del sitio del proyecto de SharePoint en Visual Studio coincide con la dirección URL que está asignada a la zona predeterminada para las asignaciones de acceso alternativas de la aplicación web. No se resuelve el error si se usa otra zona, como la intranet, para la dirección URL. La dirección URL del sitio del proyecto y la dirección URL de la zona predeterminada deben coincidir. Para acceder a las asignaciones de acceso alternativas, abra la utilidad de administración central de SharePoint 2010, elija el vínculo **Administración de aplicaciones** y, a continuación, en **aplicaciones web**, elija el vínculo **configurar asignaciones de acceso alternativas** . Para obtener más información, vea [crear zonas para aplicaciones web](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263087(v=office.12)).

## <a name="see-also"></a>Vea también

- [Solucionar problemas de empaquetado e implementación de SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md) (Compilar y depurar las soluciones de SharePoint)
- [Depurar en Visual Studio](../debugger/debugger-feature-tour.md)