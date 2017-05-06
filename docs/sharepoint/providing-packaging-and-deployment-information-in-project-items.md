---
title: "Proporcionar informaci&#243;n de empaquetado e implementaci&#243;n en los elementos del proyecto"
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
  - "VS.SharePointTools.Project.SafeControlEntries"
  - "VS.SharePointTools.Project.ProjectOutputReference"
  - "VS.SharePointTools.Project.FeatureProperties"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "propiedades de características [desarrollo de SharePoint en Visual Studio]"
  - "receptor de características [desarrollo de SharePoint en Visual Studio]"
  - "referencias de salida del proyecto [desarrollo de SharePoint en Visual Studio]"
  - "controles seguros [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, herramientas para paquetes avanzadas"
  - "desarrollo de SharePoint en Visual Studio, propiedades de características"
  - "desarrollo de SharePoint en Visual Studio, receptor de características"
  - "desarrollo de SharePoint en Visual Studio, referencias de salida del proyecto"
  - "desarrollo de SharePoint en Visual Studio, controles seguros"
ms.assetid: 209ff3b9-d701-4d27-9d24-005fcc811cbe
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Proporcionar informaci&#243;n de empaquetado e implementaci&#243;n en los elementos del proyecto
  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], todos los elementos de proyecto de SharePoint tienen propiedades que se pueden usar para proporcionar datos adicionales cuando el proyecto se implementa en SharePoint.  Estas propiedades son las siguientes:  
  
-   Propiedades de características  
  
-   Feature Receiver  
  
-   Referencias de salida del proyecto  
  
-   Entradas de controles seguros  
  
 Estas propiedades aparecen en la ventana **Propiedades**.  
  
## Propiedades de características  
 Use la propiedad **Feature Properties** para especificar los datos que la característica utiliza.  Los datos de Feature Properties son un conjunto de valores \(almacenados como pares clave\-valor\) que se incluye con una característica cuando se implementa en SharePoint.  Una vez implementada la característica, se puede obtener acceso a los valores de propiedad en el código.  
  
 Cuando se agrega un valor de propiedad de característica a un elemento de proyecto, el valor se agrega como elemento en el manifiesto de la característica del elemento.  En un proyecto del modelo Conectividad a datos profesionales \(BDC\), por ejemplo, la propiedad de característica ModelFileName aparece como:  
  
```  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 Después de establecer un valor de propiedad de característica, este se agrega como elemento en el archivo .spdata del proyecto.  Para obtener información sobre el acceso a las propiedades de SharePoint, vea [Clase de SPFeaturePropertyCollection](http://go.microsoft.com/fwlink/?LinkId=177391).  
  
 Los valores de propiedad de característica que son idénticos en todos los elementos de proyecto se combinan en el manifiesto de la característica.  Sin embargo, si dos elementos de proyecto diferentes especifican la misma clave de propiedad de característica con valores que no coinciden, se produce un error de validación.  
  
 Para agregar propiedades de característica directamente al archivo de características \(\*.feature\), llame al método <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A> del modelo de objetos de SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Si usa este método, tenga presente que la regla sobre la especificación de valores de propiedad de característica idénticos en Feature Properties también se aplica a las propiedades que se agregan directamente al archivo de características.  
  
## Receptor de características  
 Los receptores de características conforman un código que se ejecuta cuando se producen ciertos eventos en un elemento de proyecto que contiene la característica.  Por ejemplo, se pueden definir receptores de características que se ejecuten al instalar, activar o actualizar la característica.  Uno de los mecanismos para agregar un receptor de características consiste en incluirlo directamente en una característica, tal y como se describe en [Tutorial: Agregar receptores de eventos de características](../sharepoint/walkthrough-add-feature-event-receivers.md).  Otro mecanismo consiste en incluir una referencia al nombre de clase y al ensamblado de un receptor de características en la propiedad **Feature Receiver**.  
  
### Método directo  
 Cuando se agrega directamente un receptor de características a una característica, se sitúa un archivo de código bajo el nodo **Feature** del Explorador de soluciones.  Al compilar la solución de SharePoint, el código se compila en un ensamblado y se implementa en SharePoint.  De forma predeterminada, las propiedades de característica **Receiver Assembly** y **Receiver Class** hacen referencia al ensamblado y al nombre de clase.  
  
### Método de referencia  
 Otro mecanismo para agregar un receptor de características consiste en usar la propiedad **Feature Receiver** de un elemento de proyecto para hacer referencia a un ensamblado del receptor de características.  El valor de propiedad Feature Receiver tiene dos subpropiedades: **Assembly** y **Class Name**.  El ensamblado debe usar el nombre seguro y completo y el nombre de clase debe ser el nombre de tipo completo.  Para obtener más información, vea [Ensamblados Fuerte\- denominadas](http://go.microsoft.com/fwlink/?LinkID=169573).  Después de implementar la solución en SharePoint, la característica usa el receptor de características al que se hace referencia para administrar los eventos de características.  
  
 Durante la compilación de la solución, los valores de propiedad del receptor de la característica y sus proyectos se combinan para establecer los atributos ReceiverAssembly y ReceiverClass del elemento de la característica en el manifiesto de la característica del archivo \(.wsp\) de la solución de SharePoint.  Por tanto, si se especifican los valores de propiedad Assembly y Class Name de un elemento de proyecto y de una característica, los valores de propiedad del elemento de proyecto y de la característica tienen que coincidir.  Si los valores no coinciden, se producirá un error de validación.  Si desea que un elemento de proyecto haga referencia a un ensamblado del receptor de características distinto del que utiliza la característica, muévalo a otra característica.  
  
 Si hace referencia a un ensamblado del receptor de características que aún no se encuentra en el servidor, deberá incluir también el propio archivo de ensamblado en el paquete, ya que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] no lo agrega.  Cuando implemente la característica, el archivo de ensamblado se copiará en la memoria [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] o en la carpeta Bin del sistema del directorio físico de SharePoint.  Para obtener más información, vea [Cómo: Agregar y quitar ensamblados adicionales](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Para obtener más información sobre los receptores de características, vea [Receptor de eventos de característica](http://go.microsoft.com/fwlink/?LinkID=169574) y [Eventos de característica](http://go.microsoft.com/fwlink/?LinkID=169575).  
  
## Referencias de salida del proyecto  
 La propiedad Project Output References especifica una dependencia \(un ensamblado, por ejemplo\) que el elemento de proyecto necesita ejecutar.  Supongamos, por ejemplo, que su solución tiene un proyecto de BDC y un proyecto de clase.  Si el proyecto de BDC tiene una dependencia en el ensamblado generada por el proyecto de clase, puede hacer referencia al ensamblado en la propiedad Project Output References del proyecto de BDC.  Cuando el proyecto de BDC se empaqueta, el ensamblado dependiente se incluye en el paquete.  
  
 Las referencias de salida del proyecto normalmente son ensamblados, aunque en ciertos casos \(como en los proyectos de Silverlight\) puede tratarse de otros tipos de archivo.  
  
 Para obtener más información, vea [Cómo: Agregar una referencia de salida del proyecto](../sharepoint/how-to-add-a-project-output-reference.md).  
  
## Entradas de controles seguros  
 SharePoint proporciona un mecanismo de seguridad denominado entradas de controles seguros para limitar el acceso de los usuarios que no son de confianza a ciertos controles.  Por diseño, SharePoint permite que los usuarios que no son de confianza carguen y creen páginas ASPX en el servidor de SharePoint.  Para impedir que estos usuarios agreguen código no seguro a las páginas ASPX, SharePoint limita su acceso a los *controles seguros*.  Los controles seguros son elementos web y controles ASPX designados como seguros que cualquier usuario del sitio puede usar.  Para obtener más información, vea [Paso 4: Agregue el elemento web a la lista de Controles entries](http://go.microsoft.com/fwlink/?LinkID=171014).  
  
 Cada elemento de proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tiene **Entradas de controles seguros** propiedad denominada que tiene dos subpropiedades booleanos: **Seguro** y **Protección frente a scripts**.  La propiedad entries especifica si los usuarios que no son de confianza pueden obtener acceso a un control.  La propiedad Safe Against Script especifica si los usuarios que no son de confianza pueden ver y cambiar las propiedades de un control.  
  
 Las referencias a las entradas de controles seguros se establecen en cada ensamblado.  Para agregar entradas de controles seguros al ensamblado de un proyecto, especifíquelas en la propiedad **Safe Control Entries** del elemento de proyecto.  No obstante, también puede agregar las entradas de controles seguros a un ensamblado del proyecto a través de la pestaña **Opciones avanzadas** del **Diseñador de paquetes** cuando agregue un ensamblado adicional al paquete.  Para obtener más información, vea [Cómo: Marcar los controles como seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md) o [Registrar un ensamblado de elementos web como Control entries](http://go.microsoft.com/fwlink/?LinkID=171013).  
  
### Entradas XML para controles seguros  
 Cuando agrega una entrada de control seguro a un elemento de proyecto o al ensamblado del proyecto, se crea una referencia al manifiesto del paquete con el formato siguiente:  
  
```  
<Assemblies>  
    <Assembly Location="<assembly name>.dll"     
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>  
        <SafeControls>  
            <SafeControl Assembly="<assembly name>.dll" Namespace=  
              "<SharePoint project name>" Safe="<true/false>"     
                TypeName="<control name>"   
                SafeAgainstScript="<true/false>" />  
        </SafeControls>  
    </Assembly>  
</Assemblies>  
```  
  
## Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Utilizar módulos para incluir archivos en la solución](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  