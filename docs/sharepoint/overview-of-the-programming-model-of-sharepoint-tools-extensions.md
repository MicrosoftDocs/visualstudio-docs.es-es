---
title: "Overview of the Programming Model of SharePoint Tools Extensions"
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
  - "Visual Studio, extending tools"
  - "SharePoint development in Visual Studio, extensibility object models"
  - "SharePoint development in Visual Studio, extending tools"
ms.assetid: aec8165b-dff9-47be-82a5-3fa38e579297
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Overview of the Programming Model of SharePoint Tools Extensions
  Al crear una extensión para las herramientas de SharePoint en Visual Studio, comience por implementar una o varias de las interfaces de extensibilidad que exponen las herramientas de SharePoint.  En la mayoría de los casos, usará también otros tipos proporcionados por las herramientas de SharePoint para implementar características en la extensión.  En algunos escenarios, también se pueden usar tipos de otros modelos de objetos proporcionados por Visual Studio y SharePoint.  Debe comprender el propósito de cada uno de estos modelos de objetos y saber cómo usarlos entre sí para crear extensiones para las herramientas de SharePoint.  
  
## Extender las herramientas de SharePoint con la implementación de interfaces de extensibilidad  
 Visual Studio usa Managed Extensibility Framework \(MEF\) en .NET Framework 4 para proporcionar el modelo de extensibilidad para las herramientas de SharePoint.  MEF es una API \(se implementa en el ensamblado System.ComponentModel.Composition\) que permite a las aplicaciones exponer los puntos de extensibilidad y detectar y cargar las extensiones en tiempo de ejecución.  Para obtener más información sobre MEF, vea [Managed Extensibility Framework &#40;MEF&#41;](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
 Para extender las herramientas de SharePoint, implemente una o más de las interfaces de extensibilidad que expone Visual Studio.  También debe aplicar el atributo <xref:System.ComponentModel.Composition.ExportAttribute> y otros atributos específicos de las herramientas de SharePoint según sea necesario.  En la tabla siguiente se enumeran las interfaces que puede implementar para extender las herramientas de SharePoint.  
  
|Interfaz|Descripción|  
|--------------|-----------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Implemente esta interfaz para definir un nuevo tipo de elemento de proyecto de SharePoint.  Para obtener un ejemplo, vea [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Implemente esta interfaz para extender un tipo de elemento de proyecto de SharePoint que ya esté instalado en Visual Studio.  Para obtener un ejemplo, vea [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Implemente esta interfaz para extender los proyectos de SharePoint.  Para obtener un ejemplo, vea [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Implemente esta interfaz para definir un nuevo paso de implementación que se puede iniciar al implementar o retirar un elemento de proyecto de SharePoint.  Para obtener un ejemplo, vea [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Implemente esta interfaz para extender un nodo existente en el nodo **Conexiones de SharePoint** de la ventana **Explorador de servidores**.  Para obtener un ejemplo, vea [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Implemente esta interfaz para definir un nuevo tipo de nodo en el nodo **Conexiones de SharePoint** de la ventana **Explorador de servidores**.  Para obtener un ejemplo, vea [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Implemente esta interfaz para definir una regla de validación de características personalizada.  Para obtener un ejemplo, vea [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Implemente esta interfaz para definir una regla de validación de paquetes personalizada.  Para obtener un ejemplo, vea [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
  
 Después de implementar una extensión de las herramientas de SharePoint, debe implementar el ensamblado de extensión en un paquete de extensión de Visual Studio \(VSIX\) para que Visual Studio detecte y cargue la extensión.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Descripción de los modelos de objetos que se usan en las extensiones de las herramientas de SharePoint  
 Hay varios modelos de objetos que puede usar al crear extensiones para las herramientas de SharePoint:  
  
-   *Modelo de objetos de herramientas de SharePoint*.  Este modelo de objetos proporciona las interfaces de extensibilidad que se implementan para crear extensiones de herramientas de SharePoint y otros tipos relacionados.  
  
-   *Modelos de objetos de integración y automatización de Visual Studio*.  Use estos modelos de objetos para acceder a las características de Visual Studio que quedan fuera del ámbito del modelo de objetos de herramientas de SharePoint.  
  
    > [!NOTE]  
    >  Puede convertir algunos objetos del modelo de objetos de herramientas de SharePoint a los objetos de los modelos de integración y automatización de Visual Studio, y viceversa, con el servicio del proyecto de SharePoint.  Para obtener más información, consulte [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
-   *Modelos de objetos de servidor y cliente de SharePoint*.  Use estos modelos de objetos para modificar un sitio de SharePoint o para recuperar datos de un sitio de SharePoint desde el contexto de una extensión de herramientas de SharePoint.  
  
### Modelo de objetos de herramientas de SharePoint  
 Cada extensión de herramientas de SharePoint usa los tipos del modelo de objetos de herramientas de SharePoint para definir el comportamiento básico y la funcionalidad de la extensión.  En la tabla siguiente se describen los espacios de nombres que se incluyen en este modelo de objetos.  
  
|Ensamblado|Espacio de nombres|Descripción|  
|----------------|------------------------|-----------------|  
|Microsoft.VisualStudio.SharePoint.dll|<xref:Microsoft.VisualStudio.SharePoint>|Contiene los tipos que se usan para extender el sistema de proyectos de SharePoint.  Por ejemplo, puede extender elementos de proyecto y proyectos SharePoint integrados, o puede crear sus propios elementos de proyecto.  Para obtener más información, vea [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Contiene los tipos que se usan para extender el proceso de implementación de los proyectos de SharePoint, por ejemplo, para crear sus propios pasos y configuraciones de implementación.  Para obtener más información, vea [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Contiene los tipos que se usan para extender los nodos en el nodo **Conexiones de SharePoint** de la ventana **Explorador de servidores** o para definir nuevos tipos de nodos.  Para obtener más información, vea [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Features>|Contiene los tipos que se usan para acceder a la definición de una característica en un proyecto de SharePoint.|  
||<xref:Microsoft.VisualStudio.SharePoint.Packages>|Contiene los tipos que se usan para acceder a la definición del paquete de una solución de SharePoint.|  
||<xref:Microsoft.VisualStudio.SharePoint.Validation>|Contiene los tipos que se usan para personalizar el comportamiento de validación de paquetes y características de los proyectos de SharePoint.  Para obtener más información, vea [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|Microsoft.VisualStudio.SharePoint.Commands.dll|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Contiene tipos que se pueden usar para crear *comandos de SharePoint* personalizados.  Un comando de SharePoint es un método que llama al modelo de objetos de servidor de SharePoint desde una extensión de herramientas de SharePoint.  Para obtener más información, vea [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).|  
|Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Contiene tipos que se pueden usar para obtener información sobre los nodos integrados del **Explorador de servidores** que representan los componentes individuales de un sitio de SharePoint, como un nodo que represente una lista, un campo o un tipo de contenido.  Para obtener más información, vea [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
  
### Modelo de objetos de automatización de Visual Studio  
 El modelo de objetos de automatización de Visual Studio proporciona las API que se pueden usar para automatizar proyectos de Visual Studio y el IDE.  Use el modelo de objetos de Visual Studio para llevar a cabo tareas relacionadas con el proyecto que no son específicas de proyectos de SharePoint u otras tareas de automatización generales de Visual Studio.  Tradicionalmente, este modelo de objetos se suele usar en las macros y complementos de Visual Studio, pero también se puede usar en las extensiones de herramientas de SharePoint.  
  
 La parte principal del modelo de objetos de automatización de Visual Studio se define en el ensamblado EnvDTE.dll.  Los ensamblados Envdte80.DL, EnvDTE90.dll, EnvDTE100.dll y EnvDTE110.dll ofrecen una funcionalidad adicional que se introdujo en Visual Studio 2005, Visual Studio 2008, Visual Studio 2010 y [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], respectivamente.  Estos ensamblados se incluyen en Visual Studio.  
  
 Para obtener más información sobre el modelo de objetos de automatización, vea [Ampliar el entorno de Visual Studio](http://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792) y [Referencia de automatización y extensibilidad](http://msdn.microsoft.com/library/93112562-db21-4188-9383-ed19ad79bddf).  
  
### Modelo de objetos de integración de Visual Studio  
 El modelo de objetos de integración proporciona API que se pueden usar para agregar características a Visual Studio creando un *VSPackage*.  Un VSPackage es un módulo que extiende el IDE de Visual Studio proporcionando características personalizadas como ventanas de herramientas, editores, diseñadores, servicios y proyectos.  
  
 Puede usar el modelo de objetos de integración para agregar una nueva característica de Visual Studio que se use con las herramientas integradas de SharePoint.  Por ejemplo, si crea un elemento de proyecto de SharePoint personalizado que representa una acción personalizada para un sitio de SharePoint, también puede crear un VSPackage que implemente un diseñador para la acción personalizada.  Para asociar el diseñador a la acción personalizada, agregue un elemento de menú contextual para el elemento de proyecto que la representa en el **Explorador de soluciones**.  Para abrir el diseñador, abra su menú contextual \(haciendo clic con el botón derecho en el elemento de proyecto de la acción personalizada o seleccionándola y eligiendo la combinación de teclas MAYÚS \+ F10\) y, después, elija **Abrir**.  
  
 Este modelo de objetos se define en un conjunto de ensamblados que se incluyen en el SDK de Visual Studio.  Algunos de los ensamblados principales de este modelo de objetos incluyen Microsoft.VisualStudio.Shell.11.0.dll, Microsoft.VisualStudio.Shell.Interop.dll y Microsoft.VisualStudio.OLE.Interop.dll.  
  
 Para obtener más información sobre el modelo de objetos de integración, vea [Arquitectura de extensibilidad de Visual Studio](/visual-cpp/misc/visual-studio-extensibility-architecture) y [Referencia del SDK de Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
### Modelos de objetos de SharePoint  
 Las extensiones de herramientas de SharePoint pueden usar las API de SharePoint para modificar un sitio de SharePoint o para recuperar datos de un sitio de SharePoint.  [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] y [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] proporcionan dos modelos de objetos diferentes: un modelo de objetos de servidor y un modelo de objetos de cliente.  
  
 Puede usar las API en cualquier modelo de objetos de una extensión de herramientas de SharePoint, pero cada uno tiene sus ventajas y desventajas en el contexto de las extensiones de herramientas de SharePoint.  Para obtener más información, vea [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
|Modelo de objetos|Descripción|  
|-----------------------|-----------------|  
|Modelo de objetos de servidor|El modelo de objetos de servidor proporciona acceso a todas las características que [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] y [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] exponen mediante programación.  Este modelo de objetos está diseñado para su uso en soluciones de SharePoint que se inician en el servidor de SharePoint.  La mayor parte de este modelo de objetos se define en el ensamblado Microsoft.SharePoint.dll.  Para obtener más información sobre el modelo de objetos de servidor, vea [Uso del modelo de objetos de servidor de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796).|  
|Modelo de objetos de cliente|El modelo de objetos de cliente es un subconjunto del modelo de objetos de servidor que puede usarse para interoperar con datos de SharePoint de un servidor o cliente remoto.  Está diseñado para minimizar el número de recorridos de ida y vuelta que se deben ejecutar para realizar tareas comunes.  La mayor parte del modelo de objetos de cliente se define en los ensamblados Microsoft.SharePoint.Client.dll y Microsoft.SharePoint.Client.Runtime.dll.  Para obtener más información sobre el modelo de objetos de cliente, vea [Modelo de objetos cliente administrado](http://go.microsoft.com/fwlink/?LinkId=177797).|  
  
## Vea también  
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)  
  
  