---
title: "Extending SharePoint Project Items"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: f09f6664-196d-46d6-819f-3c6500f23536
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Extending SharePoint Project Items
  Cree una extensión de elemento de proyecto cuando desee agregar funcionalidad a un tipo de proyecto de SharePoint que ya se encuentra instalado en Visual Studio.  Por ejemplo, puede crear una extensión para el **Receptor de eventos** integrado o elementos de proyecto de **Definición de lista** en Visual Studio o puede crear una extensión para un tipo de elemento de proyecto personalizado.  También puede crear una extensión para todos los tipos de elementos de proyecto de SharePoint.  
  
## Tareas para extender los elementos de proyecto de SharePoint  
 Para extender un elemento de proyecto, compile un ensamblado de extensión de Visual Studio que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  Para obtener más información, vea [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 Al extender un elemento de proyecto, también puede agregar la siguiente funcionalidad al elemento de proyecto:  
  
-   Agregue un elemento de menú contextual al elemento de proyecto.  El elemento de menú aparece al abrir el menú contextual para el elemento de proyecto en **Explorador de soluciones**.  Abra el menú contextual haciendo clic con el botón secundario en el elemento de proyecto o eligiendo y elige las claves de cambio \+ de la F10.  Para obtener más información, vea [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
-   Agregue una propiedad personalizada al elemento de proyecto.  La propiedad aparece en la ventana **Propiedades** cuando se elige el elemento de proyecto en **Explorador de soluciones**.  Para obtener más información, vea [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
 Encontrará un tutorial que describe cómo crear, implementar y probar una extensión de elemento de proyecto en [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## Entender la relación entre las extensiones de elemento de proyecto y las instancias de elemento de proyecto  
 Al crear una extensión de elemento de proyecto, Visual Studio carga su extensión cuando se agrega un elemento de proyecto del tipo asociado a un proyecto de SharePoint.  Por ejemplo, si crea una extensión para los elementos de proyecto de **Receptor de eventos**, Visual Studio carga su extensión cuando un usuario agrega un elemento de proyecto de **Receptor de eventos** a un proyecto.  Visual Studio usa la misma instancia de la extensión para todas las instancias del tipo de elemento de proyecto asociado.  En el ejemplo anterior, si el usuario agrega un segundo elemento de proyecto de **Receptor de eventos** al proyecto, la misma instancia de su extensión se utiliza para personalizar el segundo elemento de proyecto.  
  
 Para obtener acceso a una instancia concreta del tipo de elemento de proyecto que se está extendiendo, controle uno de los eventos <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> del parámetro *projectItemType* en su implementación del método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>.  Por ejemplo, para determinar cuándo se agrega a un proyecto un elemento de proyecto del tipo que se está extendiendo, controle el evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>.  Para obtener más información, vea [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## Identificadores para los elementos de proyecto de SharePoint  
 Cada elemento de proyecto de SharePoint tiene un identificador de cadena correspondiente.  Debe conocer el identificador de un elemento de proyecto si desea realizar las tareas siguientes:  
  
-   Cree una extensión para el elemento de proyecto.  En este caso, debe pasar el identificador del elemento de proyecto que desea extender al constructor de la clase <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  Para crear una extensión para todos los tipos de elemento de proyecto, pase el valor de cadena **\***.  
  
-   Agregue el elemento de proyecto a un proyecto mediante programación.  En este caso, debe pasar el identificador del elemento de proyecto al método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A>.  
  
 La tabla siguiente se enumeran los identificadores de elementos de proyecto de SharePoint incluidos en Visual Studio.  
  
|Nombre del elemento de proyecto|Identificador de cadena|  
|-------------------------------------|-----------------------------|  
|Modelo de catálogo de datos profesionales|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|Tipo de contenido|Microsoft.VisualStudio.SharePoint.ContentType|  
|Receptor de eventos|Microsoft.VisualStudio.SharePoint.EventHandler|  
|Elemento vacío|Microsoft.VisualStudio.SharePoint.GenericElement|  
|Definición de lista<br /><br /> Definición de lista a partir del tipo de contenido|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|Instancia de lista|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Módulo|Microsoft.VisualStudio.SharePoint.Module|  
|Flujo de trabajo secuencial<br /><br /> Flujo de trabajo de equipo de estado|Microsoft.VisualStudio.SharePoint.Workflow|  
|Definición de sitio|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|Elemento web visual|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Elemento web|Microsoft.VisualStudio.SharePoint.WebPart|  
|Formulario de asociación de flujo de trabajo|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## Vea también  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  