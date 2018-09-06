---
title: Propiedades de MSBuild compatibles con SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1695a23ba9dddc27a37f23c714678fe6b779d328
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674395"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Propiedades de MsBuild compatibles con SharePoint
  Cualquier [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propiedad definido en el archivo Microsoft.VisualStudio.SharePoint.targets, el archivo de proyecto o el archivo de proyecto de usuario se puede utilizar en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] los proyectos de SharePoint. Además de los archivos [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propiedades proporcionadas por el proyecto de SharePoint define propiedades adicionales que son específicas de proyectos de SharePoint.  
  
 Para obtener una lista de common [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propiedades, consulte [propiedades comunes de proyectos de MSBuild](http://go.microsoft.com/fwlink/?LinkID=168687). Para obtener una lista completa de las propiedades admitidas por el lenguaje de programación, busque en el *.targets* , el archivo de proyecto (*.csproj* o *.vbproj*), o el usuario de proyecto de archivos () *csproj.user* o *. vbproj.user*).  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>Propiedades de MsBuild específicas de SharePoint
 La siguiente tabla enumera [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] propiedades que se aplican específicamente a los proyectos de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Existen otras propiedades, pero son para uso interno.  
  
|Nombre de la propiedad|Descripción|  
|-------------------|-----------------|  
|SharePointSiteUrl|Una cadena que representa el [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] al sitio de SharePoint.|  
|SandboxedSolution|Un valor booleano que indica si la solución es una solución en espacio aislado.|  
|ActiveDeploymentConfiguration|La configuración de implementación activa.|  
|IncludeAssemblyInPackage|Un valor booleano que indica si el ensamblado está incluido en el archivo de paquete.|  
|PreDeploymentCommand|Valor de cadena que representa el comando se ejecute en el paso del comando anterior a la implementación.|  
|PostDeploymentCommand|Valor de cadena que representa el comando se ejecute en el paso del comando posterior a la implementación.|  
|CustomBeforeSharePointTargets|Una cadena que representa la ruta de acceso de un [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] archivo de destinos. Si el archivo de destinos existe y está definido, se importa antes de cualquier dato de destinos de SharePoint. Esta propiedad le permite personalizar el proceso de empaquetado por propiedades relacionadas con el empaquetado predefiniendo sin modificar el archivo de destinos de SharePoint, aunque el archivo de destinos aún se aplica a todos los proyectos de SharePoint.|  
|CustomAfterSharePointTargets|Una cadena que representa la ruta de acceso de un [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] archivo de destinos. Si el archivo de destinos existe y está definido, se importa después de todos los destinos datos de SharePoint. Esta propiedad le permite personalizar el proceso de empaquetado invalidando los destinos y propiedades relacionados con el empaquetado sin tener que modificar el archivo de destinos de SharePoint, aunque el archivo de destinos aún se aplica a todos los proyectos de SharePoint.|  
|LayoutPath|Una cadena que representa el directorio raíz donde cada uno de los archivos del paquete se encuentran temporalmente antes de agregarlos a la *.wsp* archivo. Esta ruta de acceso puede ser útil saber al invalidar los destinos BeforeLayout y AfterLayout para agregar, quitar o modificar los archivos del paquete, porque puede utilizar para modificar el contenido de la *.wsp* archivo.|  
|BasePackagePath|Una cadena que representa la carpeta en la que se coloca el paquete. Este valor usa el directorio de salida del proyecto, como Bin\Debug.|  
|PackageExtension|Una cadena que representa la extensión de nombre de archivo que se anexará al paquete. El valor predeterminado es wsp.|  
|AssemblyDeploymentTarget|Una cadena que representa la ubicación donde se implementa el ensamblado del proyecto en el servidor de SharePoint. Su valor es GlobalAssemblyCache (predeterminado) o WebApplication. También se puede establecer esta propiedad en la ventana Propiedades.|  
|PackageWithValidation|Un valor booleano que especifica si se realiza la validación antes de empaquetar. Esta propiedad permite omitir los errores de validación durante la compilación de paquetes.|  
|ValidatePackageDependsOn|Cadena que define otros destinos adicionales para ejecutar antes que el destino ValidatePackage.|  
|TokenReplacementFileExensions|Una cadena que define los archivos que tienen su token se reemplazan durante el empaquetado.|  
  
## <a name="use-msbuild-properties-in-the-properties-page"></a>Utilice las propiedades de MsBuild en la página de propiedades
 Para mayor flexibilidad, en lugar de usar cadenas codificadas de forma rígida en el **línea de comandos anterior a la implementación** y **implementación posterior a la línea de comandos** cuadros en la página de propiedades de SharePoint, puede usar SharePoint propiedades como argumentos. Por ejemplo, en lugar de especificar un determinado [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] cadena para el sitio de SharePoint, puede usar en su lugar `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  Puede usar el [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] sintaxis de la variable `$(` *propertyName* `)` o la sintaxis de la variable de entorno `%` *propertyName* `%` para especificar una propiedad.  
  
## <a name="see-also"></a>Vea también
 [Referencia de MSBuild](/visualstudio/msbuild/msbuild-reference)  
  