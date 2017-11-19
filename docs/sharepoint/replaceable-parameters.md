---
title: "Parámetros reemplazables | Documentos de Microsoft"
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
ms.assetid: 3c46bbb1-0a98-495c-9fd1-dc57a6aedc11
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 80f9770fe0e6a0294ec43e450acc75f55b8ddbe2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="replaceable-parameters"></a>Parámetros reemplazables
  Parámetros reemplazables, o *tokens*, puede usarse dentro de los archivos de proyecto para proporcionar valores para los elementos de la solución de SharePoint cuyos valores reales no se conocen en tiempo de diseño. Únicamente son una función similar a la norma [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tokens de la plantilla. Para obtener más información, consulte [parámetros de plantilla](/visualstudio/ide/template-parameters).  
  
## <a name="token-format"></a>Formato de token  
 Los tokens comienzan y terminan con un carácter de signo de dólar ($). Los tokens que se usan se reemplazan por valores reales cuando un proyecto se empaqueta en un archivo de empaquetado (.wsp) de solución de SharePoint durante la implementación. Por ejemplo, el token **$SharePoint.Package.Name$** pueda resolver con la cadena "Paquete de prueba de SharePoint".  
  
## <a name="token-rules"></a>Reglas de los tokens  
 Las siguientes reglas se aplican a los tokens:  
  
-   Símbolos (tokens) puede especificarse en cualquier parte en una línea.  
  
-   Los tokens no pueden abarcar varias líneas.  
  
-   El mismo token se puede especificar varias veces en la misma línea y en el mismo archivo.  
  
-   Los tokens diferentes pueden especificarse en la misma línea.  
  
 Los tokens que no siguen estas reglas se omiten sin proporcionar una advertencia o error.  
  
 El reemplazo de los tokens por valores de cadena se realiza inmediatamente después de la transformación de los manifiestos, por lo que las plantillas de manifiesto editadas por un usuario para usar símbolos (tokens).  
  
### <a name="token-name-resolution"></a>Resolución de nombres de símbolo (token)  
 En la mayoría de los casos, un token se resuelve en un valor específico, independientemente de donde se encuentra. Sin embargo, si el token está relacionado con un paquete o una característica, valor del token depende de dónde se encuentra. Por ejemplo, si una característica es de empaquetar una, entonces el token `$SharePoint.Package.Name$` se resuelve en el valor de "Paquete A." Si la misma función está en el paquete B, a continuación, `$SharePoint.Package.Name$` se resuelve como "Paquete B."  
  
## <a name="tokens-list"></a>Lista de tokens  
 En la tabla siguiente se enumera los tokens disponibles.  
  
|Nombre|Descripción|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|El nombre del archivo del proyecto que lo contiene, por ejemplo, "Contenedor".|  
|$SharePoint.Project.FileNameWithoutExtension$|El nombre del archivo del proyecto contenedor sin la extensión de nombre de archivo. Por ejemplo, "NuevoProy".|  
|$SharePoint.Project.AssemblyFullName$|El nombre para mostrar (nombre seguro) del proyecto que lo contiene del ensamblado de salida.|  
|$SharePoint.Project.AssemblyFileName$|El nombre del proyecto que lo contiene del ensamblado de salida.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|El nombre del proyecto que lo contiene del ensamblado, sin la extensión de nombre de archivo de salida.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|El token de clave pública del proyecto que contiene la salida del ensamblado, que se convierte en una cadena. (16 caracteres en "x2" formato hexadecimal.)|  
|$SharePoint.Package.Name$|El nombre del paquete que lo contiene.|  
|$SharePoint.Package.FileName$|El nombre del archivo de definición del paquete que lo contiene.|  
|$SharePoint.Package.FileNameWithoutExtension$|El nombre (sin extensión) del archivo de definición del paquete que lo contiene.|  
|$SharePoint.Package.Id$|El identificador de SharePoint para el paquete contenedor. Si se usa una característica en más de un paquete, este valor cambiará.|  
|$SharePoint.Feature.FileName$|El nombre del archivo de definición de la característica que lo contiene, por ejemplo, Feature1.feature.|  
|$SharePoint.Feature.FileNameWithoutExtension$|El nombre del archivo de definición de función, sin la extensión de nombre de archivo.|  
|$SharePoint.Feature.DeploymentPath$|El nombre de la carpeta que contiene la característica en el paquete. Este token equivale a la propiedad "Ruta de acceso de implementación" en el Diseñador de características. Es de un valor de ejemplo, "Project1_Feature1".|  
|$SharePoint.Feature.Id$|El identificador de SharePoint de la característica de contenedor. Este token, como con todos los tokens de nivel de característica, se pueden usar únicamente por los archivos incluidos en un paquete a través de una característica, no agregar directamente a un paquete fuera de una característica.|  
|$SharePoint.ProjectItem.Name$|El nombre del elemento de proyecto (no su nombre de archivo), obtenido de **ISharePointProjectItem.Name**.|  
|$SharePoint.Type. \<GUID >. AssemblyQualifiedName$|El nombre del ensamblado de la coincidencia de tipo el [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] del token. El formato de la [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] es en minúscula y se corresponde con el formato de GUID.ToString (es decir, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
|$SharePoint.Type. \<GUID >. FullName$|El nombre completo del tipo que coincide con el GUID en el token. El formato del GUID es en minúscula y se corresponde con el formato de GUID.ToString (es decir, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|  
  
## <a name="adding-extensions-to-the-token-replacement-file-extensions-list"></a>Lista de extensiones de archivo de agregar extensiones al reemplazo del Token  
 Aunque teóricamente se pueden usar tokens en cualquier archivo que pertenece a un proyecto de SharePoint elemento incluido en el paquete, de forma predeterminada, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] busca tokens solo en archivos de paquete, los archivos de manifiesto y archivos que tienen las siguientes extensiones:  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Elemento Web  
  
-   DWP  
  
 Estas extensiones se definen mediante el `<TokenReplacementFileExtensions>` elemento en el archivo Microsoft.VisualStudio.SharePoint.targets, ubicado en el... \\< archivos de programa\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools carpeta.  
  
 Sin embargo, puede agregar extensiones de archivo adicionales a la lista. Para ello, agregue un `<TokenReplacementFileExtensions>` elemento a todos los elementos PropertyGroup en el archivo de proyecto de SharePoint que está definido antes de la \<importación > del archivo de destinos de SharePoint.  
  
> [!NOTE]  
>  Como reemplazo del token se produce una vez compilado un proyecto, no debe agregar las extensiones de archivo para tipos de archivo que se compilan, como. cs, .vb o .resx. Los tokens se reemplazan únicamente en los archivos que no se compilan.  
  
 Por ejemplo, para agregar las extensiones de nombre de archivo ".myextension" y ".yourextension" a la lista de extensiones de nombre de archivo de reemplazo del token, agregaría lo siguiente en un archivo .csproj:  
  
```  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 Como alternativa, puede agregar la extensión directamente al archivo .targets. Sin embargo, esto modifica la lista de extensiones para todos los proyectos de SharePoint empaquetados en el sistema local, no solo su propia. Esto puede ser conveniente cuando es el único desarrollador en el sistema o si así lo requiere la mayoría de los proyectos. Sin embargo, dado que es específica del sistema, este enfoque no resulta muy portátil y, por lo tanto, se recomienda que agregará todas las extensiones al archivo de proyecto en su lugar.  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  