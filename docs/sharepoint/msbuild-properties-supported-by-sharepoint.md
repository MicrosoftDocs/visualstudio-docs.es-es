---
title: "Propiedades de MSBuild compatibles con SharePoint"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, propiedades de MSBuild"
ms.assetid: 7b2b58c6-55cd-4682-a5d7-43874e70920d
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Propiedades de MSBuild compatibles con SharePoint
  Cualquier propiedad de [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] definida en el archivo Microsoft.VisualStudio.SharePoint.targets, el archivo de proyecto o el archivo de usuario del proyecto puede usarse en los proyectos de SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Además de las propiedades [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] comunes proporcionadas por el proyecto, SharePoint define otras propiedades que son específicas de los proyectos de SharePoint.  
  
 Para obtener una lista de propiedades comunes de [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] , vea [Propiedades comunes del proyecto de MSBuild](http://go.microsoft.com/fwlink/?LinkID=168687).  Para obtener una lista completa de las propiedades admitidas por su lenguaje de programación, consulte el archivo .targets, el archivo de proyecto \(.csproj o .vbproj\) o el archivo de usuario del proyecto \(csproj.user o .vbproj.user\).  
  
## Propiedades de MSBuild específicas de SharePoint  
 En la tabla siguiente se muestran las propiedades de [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] que se aplican específicamente a los proyectos de SharePoint de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Existen otras propiedades, pero son solo para uso interno.  
  
|Nombre de la propiedad|Descripción|  
|----------------------------|-----------------|  
|SharePointSiteUrl|Cadena que representa la dirección [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] del sitio de SharePoint.|  
|SandboxedSolution|Valor booleano que indica si la solución es una solución en espacio aislado.|  
|ActiveDeploymentConfiguration|Configuración de implementación activa.|  
|IncludeAssemblyInPackage|Valor booleano que indica si el ensamblado está incluido en el archivo de paquete.|  
|PreDeploymentCommand|Valor de cadena que representa el comando que se va a ejecutar en el paso del comando anterior a la implementación.|  
|PostDeploymentCommand|Valor de cadena que representa el comando que se va a ejecutar en el paso del comando posterior a la implementación.|  
|CustomBeforeSharePointTargets|Cadena que representa la ruta de acceso de un archivo de destinos de [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)].  Si el archivo de destinos existe y está definido, se importa antes que los datos de destinos de SharePoint.  Esta propiedad permite personalizar el proceso de empaquetado predefiniendo las propiedades relacionadas con el empaquetado sin necesidad de modificar el archivo de destinos de SharePoint, que sigue aplicándose a todos los proyectos de SharePoint.|  
|CustomAfterSharePointTargets|Cadena que representa la ruta de acceso de un archivo de destinos de [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)].  Si el archivo de destinos existe y está definido, se importa después de todos los datos de destinos de SharePoint.  Esta propiedad permite personalizar el proceso de empaquetado invalidando los destinos y las propiedades relacionadas con el empaquetado sin necesidad de modificar el archivo de destinos de SharePoint, que sigue aplicándose a todos los proyectos de SharePoint.|  
|LayoutPath|Cadena que representa el directorio raíz en el que los archivos que se van a empaquetar se sitúan temporalmente antes de que se agreguen al archivo .wsp.  Esta ruta de acceso puede resultar útil al invalidar los destinos de BeforeLayout y AfterLayout para agregar, quitar o modificar los archivos que se van a empaquetar, ya que puede usarse para modificar el contenido del archivo .wsp.|  
|BasePackagePath|Cadena que representa la carpeta en la que se sitúa el paquete.  Este valor usa el directorio de salida del proyecto, por ejemplo Bin\\Debug.|  
|PackageExtension|Cadena que representa la extensión de nombre de archivo que se va a anexar al paquete.  El valor predeterminado es wsp.|  
|AssemblyDeploymentTarget|Cadena que representa la ubicación en la que el ensamblado del proyecto se implementa en el servidor de SharePoint.  Su valor es GlobalAssemblyCache \(predeterminado\) o WebApplication.  Esta propiedad también se puede establecer en la ventana Propiedades.|  
|PackageWithValidation|Valor booleano que especifica si la validación se realiza antes de empaquetar.  Esta propiedad permite omitir los errores de validación que se producen al compilar paquetes.|  
|ValidatePackageDependsOn|Cadena que define otros destinos adicionales que se van a ejecutar antes del destino de ValidatePackage.|  
|TokenReplacementFileExensions|Cadena que define los archivos cuyos token se reemplazan durante el proceso de empaquetado.|  
  
## Usar las propiedades de MSBuild en el página de propiedades  
 A efectos de flexibilidad, en lugar de usar cadenas codificadas de forma rígida en los cuadros **Línea de comandos anterior a la implementación** y **Línea de comandos posterior a la implementación** de la página de propiedades de SharePoint, puede usar las propiedades de SharePoint como argumentos.  Por ejemplo, en lugar de especificar una cadena [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] concreta para el sitio de SharePoint, puede usar `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  Para especificar una propiedad, puede usar la sintaxis de la variable [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] `$(`*propertyName*`)` o la sintaxis de la variable de entorno `%`*propertyName*`%`.  
  
## Vea también  
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)  
  
  