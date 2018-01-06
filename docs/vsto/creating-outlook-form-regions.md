---
title: "Crear áreas de formulario de Outlook | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio]
- form regions [Office development in Visual Studio], creating
- Outlook [Office development in Visual Studio], form regions
ms.assetid: a8005641-cc8b-4e07-8dca-294327cdc8d4
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 357da47a68e3ae25fcd30f9516ce0509b9717807
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="creating-outlook-form-regions"></a>Creating Outlook Form Regions
  Puede usar las áreas de formulario para personalizar los formularios de Microsoft Office Outlook. Visual Studio proporciona herramientas avanzadas que facilitan el diseño, el desarrollo y la depuración de las áreas de formulario.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 En este tema se proporciona la información siguiente:  
  
-   [Ventajas de usar áreas de formulario](#Enhance)  
  
-   [Agregar un área de formulario de Outlook al proyecto](#Adding)  
  
-   [Usar el Diseñador de áreas de formulario](#UsingFormRegionDesigner)  
  
-   [Usar un área de formulario diseñado en Outlook](#UsingFormRegionDesignedOutlook)  
  
-   [Agregar código personalizado a un área de formulario](#AddingCustomCode)  
  
-   [Compilar el proyecto](#Building)  
  
-   [Depurar un área de formulario](#Debugging)  
  
-   [Implementar un área de formulario](#Deploying)  
  
##  <a name="Enhance"></a>Ventajas de usar áreas de formulario  
 Las áreas de formulario ofrecen muchas mejoras sobre el desarrollo tradicional de formularios de Outlook:  
  
-   Personalizar la página predeterminada de cualquier formulario estándar.  
  
-   Agregar hasta 12 páginas adicionales a cualquier formulario estándar.  
  
-   Reemplazar o mejorar cualquier formulario estándar.  
  
-   Mostrar la interfaz de usuario personalizada en el panel de lectura y en los inspectores.  
  
 Para obtener más información, consulte [personalizar las páginas de formulario y áreas de formulario](http://msdn.microsoft.com/library/office/ff869060.aspx).  
  
##  <a name="Adding"></a>Agregar un área de formulario de Outlook al proyecto  
 Puede usar el **nueva área de formulario de Outlook** Asistente para diseñar una nueva área de formulario o importar un área de formulario diseñada en Outlook. Además, si tiene un área de formulario que ha usado en otro proyecto de complemento de VSTO de Outlook, puede volver a usarla.  
  
###  <a name="CreatingFormRegion"></a>Crear un nueva área de formulario mediante el Asistente  
 Para crear un área de formulario, agregue un **área de formulario de Outlook** elemento a un proyecto de complemento de VSTO de Outlook. Esto inicia el **nueva área de formulario de Outlook** asistente.  
  
 Use el asistente para indicar si desea diseñar una nueva área de formulario o importar una diseñada en Outlook. Para obtener más información acerca de cómo diseñar un nueva área de formulario, vea [mediante el Diseñador de áreas de formulario](#UsingFormRegionDesigner). Para obtener más información sobre el uso de un área de formulario diseñado en Outlook, consulte [importar un área de formulario diseñada en Outlook](#UsingFormRegionDesignedOutlook).  
  
 Use el asistente para especificar el tipo de área de formulario que desea crear. En la siguiente tabla se describen todos los tipos de área de formulario.  
  
|Tipo de área|Descripción|  
|-----------------|-----------------|  
|Independiente|Agrega el área de formulario como una página nueva en un formulario de Outlook.|  
|Adyacente|Anexa el área de formulario a la parte inferior de la página predeterminada de un formulario de Outlook.|  
|Replacement|Agrega el área de formulario como una página nueva que reemplaza la página predeterminada de un formulario de Outlook.|  
|Reemplazar todo|Reemplaza todo el formulario de Outlook por el área de formulario.|  
  
 También puede usar el asistente para especificar las condiciones de presentación y seleccionar el tipo de formulario que se va a extender. Para obtener más información, consulte [Cómo: agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Las selecciones que haga en el asistente afectarán a las opciones que estén disponibles en otras páginas del asistente. Por ejemplo, si selecciona **adyacente** o **independiente** en el **crear una nueva área de formulario de Outlook** página, la **título** y **Descripción** campos no están disponibles en la **proporcione texto descriptivo y seleccione sus preferencias de presentación** página. Esto se debe a que Outlook no usa estos campos cuando muestra un área de formulario adyacente o independiente.  
  
#### <a name="form-region-files"></a>Archivos de áreas de formulario  
 Cuando complete la **nueva área de formulario de Outlook** asistente, Visual Studio agrega automáticamente los siguientes archivos al proyecto:  
  
-   Un archivo de código del área de formulario. Este archivo tiene el nombre que especifique para la **área de formulario de Outlook** de elemento en el **Agregar nuevo elemento** cuadro de diálogo. Agregue código para controlar los eventos del área de formulario en este archivo.  
  
-   Un archivo de código del Diseñador de áreas de formulario. Este archivo contiene código generado por el Diseñador de áreas de formulario y no debe editarse directamente.  
  
-   Un archivo de almacén de formularios de Outlook (.ofs).  
  
    > [!NOTE]  
    >  Este archivo solo se agrega al proyecto si se importa un área de formulario diseñada en Outlook.  
  
#### <a name="form-region-factory-class"></a>Clase de generador de áreas de formulario  
 El archivo de código del área de formulario contiene una clase parcial que implementa la interfaz <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory>. Se trata de la clase de generador de áreas de formulario. La clase de generador de áreas de formulario es responsable de crear nuevas instancias del área de formulario.  
  
 Puede encontrar esta clase, expanda la **generador de áreas de formulario** región.  
  
 El **nueva área de formulario de Outlook** asistente agrega los atributos para esta clase que especifican el nombre interno del área del formulario y las clases de mensaje que muestran el área de formulario. Puede modificar estos atributos manualmente una vez agregado el archivo al proyecto.  
  
 La mayor parte de la clase de generador de áreas de formulario se implementa en el archivo del Diseñador de áreas de formulario. Sin embargo, el controlador de eventos `FormRegionInitializing` se expone en el archivo de código del área de formulario. Puede usar este controlador de eventos para especificar si Outlook debe mostrar el área de formulario. Para obtener más información, consulte [control de eventos del área de formulario](#HandlingFormRegionEvents).  
  
###  <a name="AddingExistingFormRegion"></a>Agregar un área de formulario existente a un proyecto  
 Si ha usado un área de formulario de Outlook en otro proyecto de Outlook, puede volver a usarla en el proyecto de complemento de VSTO de Outlook actual mediante el cuadro de diálogo **Agregar elemento existente** .  
  
 El área de formulario existente debe tener un archivo de código (.vb o. cs); no se puede agregar archivos de almacén de formularios de Outlook (.ofs) mediante el uso de la **Agregar elemento existente** cuadro de diálogo. Sin embargo, puede crear una nueva área de formulario importando un archivo de almacén de formularios de Outlook. Para obtener más información, consulte [Cómo: agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
##  <a name="UsingFormRegionDesigner"></a>Usar el Diseñador de áreas de formulario  
 El Diseñador de áreas de formulario ayuda a establecer el diseño y la apariencia de un área de este tipo. Puede arrastrar controles administrados a la superficie del diseñador, haga doble clic en controles para abrir los controladores de eventos y establecer propiedades en el **propiedades** ventana.  
  
> [!NOTE]  
>  Puede buscar propiedades que afectan al modo en que aparece el área de formulario en Outlook bajo el **manifiesto** nodo en el **propiedades** ventana.  
  
 El Diseñador de áreas de formulario solo está disponible si selecciona **diseñar una nueva área de formulario** en el **Seleccione cómo desea crear el área de formulario** página de la **nueva área de formulario de Outlook** Asistente.  
  
 Existen tres maneras de abrir el Diseñador de áreas de formulario:  
  
-   En **el Explorador de soluciones**, haga doble clic en el archivo de código de área de formulario.  
  
-   En **el Explorador de soluciones**, haga clic en el archivo de código de área de formulario y, a continuación, haga clic en **Diseñador de vistas**.  
  
-   En **el Explorador de soluciones**, seleccione el archivo de código de área de formulario y, a continuación, en la **vista** menú, haga clic en **diseñador**.  
  
 El Diseñador de áreas de formulario solo admite controles administrados. No puede agregar controles nativos de Outlook.  
  
##  <a name="UsingFormRegionDesignedOutlook"></a>Importar un área de formulario diseñado en Outlook  
 Al diseñar en Outlook, puede agregar controles nativos de Outlook al área de formulario. Los controles nativos de Outlook permiten enlazar a datos de Outlook en tiempo de diseño. Sin embargo, después no se podrá usar el Diseñador de áreas de formulario para agregar controles administrados o cambiar el diseño del área de formulario.  
  
 Puede importar áreas de formulario en un proyecto de complemento de VSTO para Outlook mediante el **nueva área de formulario de Outlook** asistente. En el **Seleccione cómo desea crear el área de formulario** , seleccione **importar un archivo de almacén de formularios de Outlook (.ofs)**. Luego, puede examinar la ubicación de un archivo de almacén de formularios de Outlook (.ofs) (Outlook guarda las áreas de formulario como archivos .ofs).  
  
 El **nueva área de formulario de Outlook** asistente copia el archivo .ofs en el directorio del proyecto y agrega referencias de control al archivo de diseñador de área de formulario. Luego, puede controlar los eventos de control en el archivo de código del área de formulario.  
  
 Para controlar eventos en un proyecto de Visual Basic, seleccione un evento en la lista de nombres de métodos en la parte superior del Editor de código.  
  
 Para controlar eventos en un proyecto de C#, suscríbase a los eventos de control en el método <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>. Para obtener más información, vea [Cómo: Suscribir y cancelar la suscripción a eventos &#40; C &#35; Guía de programación de &#41; ](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events).  
  
 Puede cambiar las propiedades del área de formulario en el método `InitializeManifest` de la clase de generador de áreas de formulario.  
  
> [!NOTE]  
>  Para importar un área de formulario, debe estar trabajando en un proyecto destinado a la misma versión de Outlook que la que está instalada en el equipo de desarrollo. Por ejemplo, si tiene instalado Outlook 2010, la importación de un formulario región solo funcionará en un proyecto se creó mediante la **complemento de Outlook 2010** plantilla de proyecto.  
  
### <a name="updating-an-imported-form-regions-design"></a>Actualizar el diseño de un área de formulario importada  
 Puede agregar, quitar o cambiar los controles del área de formulario. Antes de hacerlo, haga una copia de seguridad del código que haya agregado al archivo de código del área de formulario. Luego, abra el archivo .ofs en Outlook, modifique el área de formulario y guarde los cambios. Use la **nueva área de formulario de Outlook** Asistente para importar el archivo .ofs modificado. Luego, puede pegar el código en el nuevo archivo de código del área de formulario.  
  
##  <a name="AddingCustomCode"></a>Agregar código personalizado a un área de formulario  
 El espacio de nombres <xref:Microsoft.Office.Tools.Outlook> proporciona acceso a las clases que representan el área de formulario, al elemento de Outlook que muestra dicha área y a otros elementos útiles. El **área de formulario de Outlook** elemento agrega automáticamente una referencia a este ensamblado en el proyecto e inserta la correspondiente **con** o **importaciones** instrucción en la parte superior de la archivo de código de área de formulario.  
  
 Puede utilizar las clases, métodos y propiedades en el espacio de nombres Microsoft.Office.Interop.Outlook para realizar la mayoría de las tareas de programación de Outlook. Para obtener más información sobre el modelo de objetos de Outlook, consulte [información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md). Para obtener ejemplos de las tareas habituales que utilizar el modelo de objetos de Outlook, consulte [soluciones de Outlook](../vsto/outlook-solutions.md).  
  
###  <a name="HandlingFormRegionEvents"></a>Control de eventos de áreas de formulario  
 El **área de formulario de Outlook** elemento agrega automáticamente los siguientes tres controladores de eventos para el archivo de código de área de formulario.  
  
|evento|Descripción|  
|-----------|-----------------|  
|FormRegionInitializing|Se produce antes de inicializarse el área de formulario. Puede comprobar las condiciones de este controlador de eventos para determinar si Outlook debe mostrar el área de formulario. Para obtener más información, consulte [Cómo: impedir que Outlook muestre un área de formulario](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|  
|FormRegionShowing|Se produce después de crear una instancia del área de formulario pero antes de que esta aparezca.|  
|FormRegionClosed|Se produce antes de cerrar el área de formulario.|  
  
##  <a name="Building"></a>Compilar el proyecto  
 Cuando se compila un proyecto de complemento de VSTO de Outlook que contiene un área de formulario, Visual Studio agrega la siguiente información al registro:  
  
-   Una clave para cada clase de mensaje asociada a una o varias áreas de formulario.  
  
-   Una entrada para cada área de formulario y un valor asociado que representa el nombre del complemento de VSTO de Outlook.  
  
 Outlook usa esta información para cargar las áreas de formulario.  
  
##  <a name="Debugging"></a>Depurar un área de formulario  
 Puede depurar un complemento de VSTO de Outlook que contiene un área de formulario tal y como lo haría con otros proyectos de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Al iniciar el depurador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Visual Studio inicia automáticamente Outlook.  
  
 Para ver el área de formulario, debe abrir el elemento de Outlook adecuado. Por ejemplo, si un área de formulario adyacente se anexa a la parte inferior de un elemento de correo, abra un elemento de correo.  
  
##  <a name="Deploying"></a>Implementar un área de formulario  
 Las áreas de formulario se implementan automáticamente con el complemento de VSTO de Outlook asociado. Por lo tanto, no es necesario efectuar ninguna tarea especial para implementar un área de formulario. Para obtener más información acerca de la implementación de complementos VSTO, consulte [implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Instrucciones para crear áreas de formulario de Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)|Proporciona información que le puede ayudar a optimizar las áreas del formulario y evitar posibles problemas.|  
|[Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Muestra cómo crear un área de formulario para extender un formulario de Microsoft Office Outlook estándar o personalizado mediante el uso de la **nueva área de formulario de Outlook** asistente.|  
|[Asociación de un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Explica cómo especificar los elementos de Microsoft Office Outlook que van a mostrar un área de formulario asociándola a la clase de mensaje de cada elemento.|  
|[Tutorial: Diseño de un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)|Muestra cómo diseñar un área de formulario personalizada que aparece como una nueva página en la ventana del inspector de un elemento de contacto.|  
|[Tutorial: Importación de un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Muestra cómo diseñar un área de formulario en Microsoft Office Outlook y, a continuación, importar el área de formulario en un proyecto de complemento de VSTO para Outlook mediante el **nueva área de formulario de Outlook** asistente.|  
|[Obtener acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)|Describe cómo escribir código para mostrar, ocultar o modificar los controles de un área de formulario y permitir a los usuarios ejecutar código de otras áreas del proyecto usando la clase `Globals`.|  
|[Cómo: Impedir que Outlook muestre un área de formulario](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Muestra cómo evitar que Microsoft Office Outlook muestre un área de formulario de un elemento determinado.|  
|Muestra cómo tener acceso al elemento de Outlook en el que aparece un área de formulario.|  
|[Acciones personalizadas en áreas de formulario de Outlook](../vsto/custom-actions-in-outlook-form-regions.md)|Describe cómo permitir que los usuarios respondan a un elemento de Outlook.|  
  
  