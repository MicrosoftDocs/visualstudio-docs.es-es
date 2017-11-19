---
title: "Información general sobre el modelo de programación de SharePoint de extensiones de herramientas | Documentos de Microsoft"
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
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
ms.assetid: aec8165b-dff9-47be-82a5-3fa38e579297
caps.latest.revision: "55"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5209ec60734213fbafb7b176d91589527b571c32
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>Información general del modelo de programación de extensiones de SharePoint
  Al crear una extensión para las herramientas de SharePoint en Visual Studio, comience por implementar una o varias de las interfaces de extensibilidad que exponen las herramientas de SharePoint. En la mayoría de los casos, usará también otros tipos proporcionados por las herramientas de SharePoint para implementar características en la extensión. En algunos escenarios, también se pueden usar tipos de otros modelos de objetos proporcionados por Visual Studio y SharePoint. Debe comprender el propósito de cada uno de estos modelos de objetos y saber cómo usarlos entre sí para crear extensiones para las herramientas de SharePoint.  
  
## <a name="extending-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>Extender las herramientas de SharePoint con la implementación de interfaces de extensibilidad  
 Visual Studio usa Managed Extensibility Framework (MEF) en .NET Framework 4 para proporcionar el modelo de extensibilidad para las herramientas de SharePoint. MEF es una API (se implementa en el ensamblado System.ComponentModel.Composition) que permite a las aplicaciones exponer los puntos de extensibilidad y detectar y cargar las extensiones en tiempo de ejecución. Para obtener más información acerca de MEF, vea [Managed Extensibility Framework &#40; MEF &#41; ](/dotnet/framework/mef/index).  
  
 Para extender las herramientas de SharePoint, implemente una o más de las interfaces de extensibilidad que expone Visual Studio. También debe aplicar el atributo <xref:System.ComponentModel.Composition.ExportAttribute> y otros atributos específicos de las herramientas de SharePoint según sea necesario. En la tabla siguiente se enumeran las interfaces que puede implementar para extender las herramientas de SharePoint.  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|Implemente esta interfaz para definir un nuevo tipo de elemento de proyecto de SharePoint. Para obtener un ejemplo, vea [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Implemente esta interfaz para extender un tipo de elemento de proyecto de SharePoint que ya esté instalado en Visual Studio. Para obtener un ejemplo, vea [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|Implemente esta interfaz para extender los proyectos de SharePoint. Para obtener un ejemplo, vea [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|Implemente esta interfaz para definir un nuevo paso de implementación que se puede iniciar al implementar o retirar un elemento de proyecto de SharePoint. Para obtener un ejemplo, vea [Tutorial: crear un paso de implementación personalizado para proyectos de SharePoint de](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|Implemente esta interfaz para extender un nodo existente en el **las conexiones de SharePoint** nodo en el **Explorador de servidores** ventana. Para obtener un ejemplo, vea [Cómo: Extender un nodo de SharePoint en el Explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|Implemente esta interfaz para definir un nuevo tipo de nodo en el **las conexiones de SharePoint** nodo en el **Explorador de servidores** ventana. Para obtener un ejemplo, vea [Cómo: Extender un nodo de SharePoint en el Explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|Implemente esta interfaz para definir una regla de validación de características personalizada. Para obtener un ejemplo, vea [Cómo: Create Custom Feature y reglas de validación de paquetes para soluciones de SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|Implemente esta interfaz para definir una regla de validación de paquetes personalizada. Para obtener un ejemplo, vea [Cómo: Create Custom Feature y reglas de validación de paquetes para soluciones de SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
  
 Después de implementar una extensión de las herramientas de SharePoint, debe implementar el ensamblado de extensión en un paquete de extensión de Visual Studio (VSIX) para que Visual Studio detecte y cargue la extensión. Para obtener más información, consulte [extensiones de implementación para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="understanding-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>Descripción de los modelos de objetos que se usan en las extensiones de las herramientas de SharePoint  
 Hay varios modelos de objetos que puede usar al crear extensiones para las herramientas de SharePoint:  
  
-   *Modelo de objetos de herramientas de SharePoint*. Este modelo de objetos proporciona las interfaces de extensibilidad que se implementan para crear extensiones de herramientas de SharePoint y otros tipos relacionados.  
  
-   *Visual Studio automatización e integración objeto los modelos*. Use estos modelos de objetos para acceder a las características de Visual Studio que quedan fuera del ámbito del modelo de objetos de herramientas de SharePoint.  
  
    > [!NOTE]  
    >  Puede convertir algunos objetos del modelo de objetos de herramientas de SharePoint a los objetos de los modelos de integración y automatización de Visual Studio, y viceversa, con el servicio del proyecto de SharePoint. Para obtener más información, consulte [convertir entre SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
-   *Los modelos de objetos de servidor y cliente de SharePoint*. Use estos modelos de objetos para modificar un sitio de SharePoint o para recuperar datos de un sitio de SharePoint desde el contexto de una extensión de herramientas de SharePoint.  
  
### <a name="sharepoint-tools-object-model"></a>Modelo de objetos de herramientas de SharePoint  
 Cada extensión de herramientas de SharePoint usa los tipos del modelo de objetos de herramientas de SharePoint para definir el comportamiento básico y la funcionalidad de la extensión. En la tabla siguiente se describen los espacios de nombres que se incluyen en este modelo de objetos.  
  
|Ensamblado|Espacio de nombres|Descripción|  
|--------------|---------------|-----------------|  
|Microsoft.VisualStudio.SharePoint.dll|<xref:Microsoft.VisualStudio.SharePoint>|Contiene los tipos que se usan para extender el sistema de proyectos de SharePoint. Por ejemplo, puede extender elementos de proyecto y proyectos SharePoint integrados, o puede crear sus propios elementos de proyecto. Para obtener más información, consulte [extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Deployment>|Contiene los tipos que se usan para extender el proceso de implementación de los proyectos de SharePoint, por ejemplo, para crear sus propios pasos y configuraciones de implementación. Para obtener más información, consulte [extender SharePoint empaquetado e implementación](../sharepoint/extending-sharepoint-packaging-and-deployment.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Explorer>|Contiene tipos que se usan para extender los nodos en el **las conexiones de SharePoint** nodo en el **Explorador de servidores** ventana, o para definir nuevos tipos de nodos. Para obtener más información, consulte [extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
||<xref:Microsoft.VisualStudio.SharePoint.Features>|Contiene los tipos que se usan para acceder a la definición de una característica en un proyecto de SharePoint.|  
||<xref:Microsoft.VisualStudio.SharePoint.Packages>|Contiene los tipos que se usan para acceder a la definición del paquete de una solución de SharePoint.|  
||<xref:Microsoft.VisualStudio.SharePoint.Validation>|Contiene los tipos que se usan para personalizar el comportamiento de validación de paquetes y características de los proyectos de SharePoint. Para obtener más información, consulte [Cómo: Create Custom Feature y reglas de validación de paquetes para soluciones de SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).|  
|Microsoft.VisualStudio.SharePoint.Commands.dll|<xref:Microsoft.VisualStudio.SharePoint.Commands>|Contiene tipos que pueden usar para crear personalizado *comandos de SharePoint*. Un comando de SharePoint es un método que llama al modelo de objetos de servidor de SharePoint desde una extensión de herramientas de SharePoint. Para obtener más información, consulte [llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|  
|Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|Contiene tipos que puede usar para obtener información sobre integrada **Explorador de servidores** nodos que representan los componentes individuales de un sitio de SharePoint, como un nodo que representa una lista, campo o tipo de contenido. Para obtener más información, consulte [extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).|  
  
### <a name="visual-studio-automation-object-model"></a>Modelo de objetos de Automation de Visual Studio  
 El modelo de objetos de automatización de Visual Studio proporciona las API que se pueden usar para automatizar proyectos de Visual Studio y el IDE. Use el modelo de objetos de Visual Studio para llevar a cabo tareas relacionadas con el proyecto que no son específicas de proyectos de SharePoint u otras tareas de automatización generales de Visual Studio. Tradicionalmente, este modelo de objetos se suele usar en las macros y complementos de Visual Studio, pero también se puede usar en las extensiones de herramientas de SharePoint.  
  
 La parte principal del modelo de objetos de automatización de Visual Studio se define en el ensamblado EnvDTE.dll. El EnvDTE*versión*los ensamblados .dll proporcionan una funcionalidad adicional que se introdujo en las versiones específicas de Visual Studio. Estos ensamblados se incluyen en Visual Studio.  
  
 Para obtener más información sobre el modelo de objetos de automatización, vea [referencia de SDK de Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
### <a name="visual-studio-integration-object-model"></a>Modelo de objetos de integración de Visual Studio  
 El modelo de objetos de integración proporciona API que puede usar para agregar características a Visual Studio creando un *VSPackage*. Un VSPackage es un módulo que extiende el IDE de Visual Studio proporcionando características personalizadas como ventanas de herramientas, editores, diseñadores, servicios y proyectos.  
  
 Puede usar el modelo de objetos de integración para agregar una nueva característica de Visual Studio que se use con las herramientas integradas de SharePoint. Por ejemplo, si crea un elemento de proyecto de SharePoint personalizado que representa una acción personalizada para un sitio de SharePoint, también puede crear un VSPackage que implemente un diseñador para la acción personalizada. Puede asociar el diseñador con la acción personalizada mediante la adición de un elemento de menú contextual para el elemento de proyecto que representa la acción personalizada en **el Explorador de soluciones**. Puede abrir el diseñador, abra el menú contextual (haciendo clic en el proyecto de acción personalizada de elemento o si lo selecciona y, a continuación, elija la tecla MAYÚS + F10 claves) y, a continuación, eligiendo **abrir**.  
  
 Este modelo de objetos se define en un conjunto de ensamblados que se incluyen en el SDK de Visual Studio. Algunos de los ensamblados principales de este modelo de objetos incluyen Microsoft.VisualStudio.Shell.11.0.dll, Microsoft.VisualStudio.Shell.Interop.dll y Microsoft.VisualStudio.OLE.Interop.dll.  
  
 Para obtener más información sobre el modelo de objetos de integración, vea [información general del modelo de automatización](/visualstudio/extensibility/internals/automation-model-overview) y [referencia de SDK de Visual Studio](/visualstudio/extensibility/visual-studio-sdk-reference).  
  
### <a name="sharepoint-object-models"></a>Modelos de objetos de SharePoint  
 Las extensiones de herramientas de SharePoint pueden usar las API de SharePoint para modificar un sitio de SharePoint o para recuperar datos de un sitio de SharePoint. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] y [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] proporcionan dos modelos de objetos diferentes: un modelo de objetos de servidor y un modelo de objetos de cliente.  
  
 Puede usar las API en cualquier modelo de objetos de una extensión de herramientas de SharePoint, pero cada uno tiene sus ventajas y desventajas en el contexto de las extensiones de herramientas de SharePoint. Para obtener más información, consulte [llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
|Modelo de objetos|Descripción|  
|------------------|-----------------|  
|Modelo de objetos de servidor|El modelo de objetos de servidor proporciona acceso a todas las características que [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] y [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] exponen mediante programación. Este modelo de objetos está diseñado para su uso en soluciones de SharePoint que se inician en el servidor de SharePoint. La mayor parte de este modelo de objetos se define en el ensamblado Microsoft.SharePoint.dll. Para obtener más información sobre el modelo de objetos de servidor, consulte [utilizando el modelo de objetos de servidor de SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=177796).|  
|Modelo de objetos de cliente|El modelo de objetos de cliente es un subconjunto del modelo de objetos de servidor que puede usarse para interoperar con datos de SharePoint de un servidor o cliente remoto. Está diseñado para minimizar el número de recorridos de ida y vuelta que se deben ejecutar para realizar tareas comunes. La mayor parte del modelo de objetos de cliente se define en los ensamblados Microsoft.SharePoint.Client.dll y Microsoft.SharePoint.Client.Runtime.dll. Para obtener más información sobre el modelo de objetos de cliente, consulte [modelo de objetos de cliente administrado](http://go.microsoft.com/fwlink/?LinkId=177797).|  
  
## <a name="see-also"></a>Vea también  
 [Extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Uso del servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md)  
  
  