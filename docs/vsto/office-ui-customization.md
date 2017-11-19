---
title: "Personalización de la interfaz de usuario de Office | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- menus [Office development in Visual Studio], customizing
- actions panes [Office development in Visual Studio], creating
- WPF [Office development in Visual Studio]
- toolbars [Office development in Visual Studio], customizing
- Office applications [Office development in Visual Studio], UI customization
ms.assetid: 3d7c7b88-2053-4ada-bfe7-e7bb202c430b
caps.latest.revision: "74"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7af3c33ed45a5e0b9678a41900280b1e665766ed
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="office-ui-customization"></a>Personalización de la interfaz de usuario de Office
  Puede personalizar la interfaz de usuario (UI) de las aplicaciones de Microsoft Office mediante el uso de las herramientas de desarrollo de Office en Visual Studio. En este tema se describen las características de la interfaz de usuario que se pueden personalizar en las secciones siguientes:  
  
-   [Comparación de las características de interfaz de usuario](#Comparison)  
  
-   [Paneles de acciones y paneles de tareas personalizados](#Actions)  
  
-   [Interfaz de usuario de cinta de opciones personalizada](#Ribbon)  
  
-   [Vista Backstage](#Backstage)  
  
-   [Áreas de formulario de Outlook](#FormRegion)  
  
-   [Controles en documentos](#Controls)  
  
-   [Menús contextuales](#Shortcut)  
  
##  <a name="Comparison"></a>Comparación de las características de interfaz de usuario  
 En la siguiente tabla se comparan las características principales de la interfaz de usuario que se pueden personalizar en los proyectos de Microsoft Office.  
  
|Característica|Tipos de proyecto compatibles|Aplicaciones de Microsoft Office compatibles|  
|-------------|-----------------------------|---------------------------------------------|  
|Panel de acciones|Personalizaciones de nivel de documento|Excel<br /><br /> Word|  
|Paneles de tareas personalizados|Complementos de VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word<br /><br /> Excel|  
|Interfaz de usuario de Cinta personalizada|Personalizaciones de nivel de documento<br /><br /> Complementos de VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> Powerpoint<br /><br /> Proyecto<br /><br /> Word<br /><br /> Visio|  
|Vista Backstage|Personalizaciones de nivel de documento<br /><br /> Complementos de VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Proyecto<br /><br /> Word<br /><br /> Visio|  
|Áreas de formulario de Outlook|Complementos de VSTO|Outlook|  
|Controles en documentos|Personalizaciones de nivel de documento<br /><br /> Complementos de VSTO|Excel<br /><br /> Word|  
|Menús contextuales|Personalizaciones de nivel de documento<br /><br /> Complementos de VSTO|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Proyecto<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|  
  
##  <a name="Actions"></a>Paneles de acciones y paneles de tareas personalizados  
 Los paneles de tareas son paneles de interfaz de usuario que normalmente están acoplados a un lado de una ventana en una aplicación de Microsoft Office. Casi todas las aplicaciones de Microsoft Office incluyen paneles de tareas integrados. Un ejemplo de un panel de tareas es el panel de tareas Ayuda de Word.  
  
 Las herramientas de desarrollo de Office en Visual Studio proporcionan dos maneras diferentes de personalizar los paneles de tareas:  
  
-   Puede agregar un panel de acciones a una personalización de nivel de documento. De forma predeterminada, el panel de acciones se muestra en el lado derecho de la aplicación, a la derecha del documento. Sin embargo, el panel de acciones también puede mostrarse en el lado izquierdo, superior o inferior del documento.  
  
-   Puede agregar un panel de tareas personalizado a un complemento de VSTO. Los usuarios pueden acoplar paneles de tareas personalizados en diferentes lados de la ventana de la aplicación o pueden arrastrar paneles de tareas personalizados a cualquier lugar de la ventana.  
  
 Los paneles de acciones y los paneles de tareas personalizados proporcionan funcionalidad mediante el hospedaje de una variedad de controles que ayudan a los usuarios a llevar a cabo tareas como la introducción de datos. En comparación con el grupo Cinta, los paneles de acciones y los paneles de tareas personalizados proporcionan un área mucho más grande en la que incluir texto y controles.  
  
 Para obtener más información acerca de los paneles de acciones, vea [información general sobre paneles de acciones](../vsto/actions-pane-overview.md). Para obtener más información acerca de los paneles de tareas personalizados, vea [los paneles de tareas personalizados](../vsto/custom-task-panes.md).  
  
##  <a name="Ribbon"></a>Interfaz de usuario de cinta de opciones personalizada  
 Puede personalizar la interfaz de usuario de la Cinta para exponer funcionalidades que agregue a las aplicaciones de Office. La Cinta es una manera de organizar comandos relacionados (en forma de controles) para que sean fáciles de encontrar. Puede crear sus propios grupos y pestañas de la Cinta para proporcionar a los usuarios acceso a las funcionalidades que se proporcionan en su solución. Ahora se puede acceder mediante la Cinta a la mayoría de las características a las que antes se accedía mediante menús y barras de herramientas en versiones anteriores de Microsoft Office system.  
  
 Para obtener más información, consulte [información general de la cinta de opciones](../vsto/ribbon-overview.md).  
  
##  <a name="Backstage"></a>Vista Backstage  
 En las aplicaciones de Office, haga clic en el **archivo** ficha abre la vista Backstage. La vista Backstage proporciona una interfaz de usuario que combina las acciones y tareas de nivel de archivo y reemplaza las funcionalidades similares a las que se podía acceder en 2007 Microsoft Office system mediante el botón de Microsoft Office. La vista Backstage es totalmente extensible mediante XML.  
  
 Visual Studio no proporciona un diseñador ni API para personalizar la vista Backstage. Sin embargo, si agrega un **cinta (XML)** elemento al proyecto de Office, puede agregar XML al archivo XML de cinta de opciones para personalizar la vista Backstage. Para obtener más información acerca de **cinta (XML)** elementos, vea [XML de cinta de opciones](../vsto/ribbon-xml.md).  
  
 Para obtener más información acerca de cómo personalizar la vista Backstage, consulte [Introducción a Office 2010 Backstage View for Developers](http://go.microsoft.com/fwlink/?LinkId=182189) y [personalizar Office 2010 Backstage View for Developers](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
##  <a name="FormRegion"></a>Áreas de formulario de Outlook  
 Utilice las áreas de formulario para agregar funcionalidades personalizadas a formularios estándar de Microsoft Office Outlook. Puede crear áreas de formulario que extiendan cualquier formulario existente mediante campos o controles adicionales. Si crea una nueva área de formulario mediante las herramientas de desarrollo de Office en Visual Studio, solo podrá utilizar controles de Windows Forms en el área de formulario. Si importa un área de formulario diseñada en Outlook, solo podrá usar controles nativos de Outlook.  
  
 Puede crear áreas de formulario que ocupen áreas diferentes de la interfaz de usuario de Outlook. Por ejemplo, las áreas de formulario adyacentes se muestran en la parte inferior de la primera página de un formulario y cada área de formulario adyacente es contraíble. También puede agregar un área de formulario independiente que se muestre como una página de formulario adicional completa y que puede aparecer en cualquier formulario estándar existente o personalizado.  
  
 Para obtener más información, consulta [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
##  <a name="Controls"></a>Controles en documentos  
 Puede agregar diversos controles a documentos de Word y hojas de cálculo de Excel. Por ejemplo, puede que le convenga agregar un control de selector de fecha a un documento para que el usuario pueda introducir fechas en un formato estándar o colocar un botón en una hoja de cálculo para enviar datos a una base de datos.  
  
 Al desarrollar proyectos de nivel de documento para Excel o Word, puede usar el diseñador de Visual Studio para agregar los controles al documento o libro del proyecto en tiempo de diseño o puede agregar controles mediante programación en tiempo de ejecución. Al desarrollar proyectos de complementos de VSTO para Excel o Word, puede agregar controles mediante programación a cualquier documento o libro abierto en tiempo de ejecución.  
  
 Para obtener más información, vea [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md) y [Windows Forms Controls on Office Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
##  <a name="Shortcut"></a>Menús contextuales  
 Cuando hace clic en un documento o una ventana de aplicación, se muestra un menú contextual. Puede establecer que aparezca un menú contextual después de que tenga lugar un evento, como, por ejemplo, cuando un usuario hace clic con el botón derecho en un documento, libro o control host. Puede agregar diversos comandos de menú o controles a un menú contextual. Cree menús contextuales mediante XML. Si agrega un **cinta (XML)** elemento al proyecto de Office, puede agregar XML al archivo XML de cinta de opciones para crear menús contextuales. Para obtener más información sobre cómo usar XML para crear menús contextuales, vea [Cómo: agregar comandos a menús contextuales](../vsto/how-to-add-commands-to-shortcut-menus.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general de la cinta de opciones](../vsto/ribbon-overview.md)   
 [Controles en documentos de Office información general sobre formularios Windows Forms](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)   
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Paneles de tareas personalizados](../vsto/custom-task-panes.md)   
 [Utilizar controles WPF en soluciones de Office](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Cómo: mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)   
 [Cómo: Mostrar errores de interfaz de usuario](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Tutorial: Recopilación de datos con Windows Forms](../vsto/walkthrough-collecting-data-using-a-windows-form.md)  
  
  