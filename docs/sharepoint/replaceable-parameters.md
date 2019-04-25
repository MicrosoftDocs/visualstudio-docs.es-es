---
title: Parámetros reemplazables | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, tokens
- tokens [SharePoint development in Visual Studio]
- replaceable parameters [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, replaceable parameters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload: office
ms.openlocfilehash: d85e125ee09d459d23b3b709f58d5af43e76e984
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611872"
---
# <a name="replaceable-parameters"></a>Parámetros reemplazables
  Parámetros reemplazables, o *tokens*, puede usar dentro de los archivos de proyecto para proporcionar valores para los elementos de la solución de SharePoint cuyos valores reales no se conocen en tiempo de diseño. Son una función similar a la norma [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tokens de la plantilla. Para obtener más información, consulte [parámetros de plantilla](../ide/template-parameters.md).

## <a name="token-format"></a>Formato de token
 Los tokens comienzan y terminan con un carácter de signo de dólar ($). En la implementación, cualquier token utilizado se reemplaza por valores reales cuando un proyecto se empaqueta en un paquete de solución de SharePoint (*.wsp* archivo). Por ejemplo, el token **$SharePoint.Package.Name$** pueda resolver con la cadena "Paquete de prueba de SharePoint".

## <a name="token-rules"></a>Reglas de los tokens
 Las siguientes reglas se aplican a los tokens:

- Los tokens se pueden especificar en cualquier parte en una línea.

- Los tokens no pueden abarcar varias líneas.

- El mismo token se puede especificar más de una vez en la misma línea y en el mismo archivo.

- En la misma línea, se pueden especificar diferentes tokens.

  Los tokens que no siguen estas reglas se omiten y no dan lugar a una advertencia o error.

  El reemplazo de tokens por los valores de cadena se realiza inmediatamente después de la transformación de los manifiestos. Este reemplazo permite al usuario editar las plantillas con tokens de manifiesto.

### <a name="token-name-resolution"></a>Resolución de nombres de token
 En la mayoría de los casos, un token se resuelve en un valor específico, independientemente de se encuentra. Sin embargo, si el token está relacionado con un paquete o una característica, valor del token depende de se encuentra. Por ejemplo, si es una característica de empaquetar una, entonces el token `$SharePoint.Package.Name$` se resuelve como el valor "Paquete de r." Si la función misma está en el paquete B, a continuación, `$SharePoint.Package.Name$` se resuelve como "Paquete b".

## <a name="tokens-list"></a>Lista de tokens
 En la tabla siguiente se enumera los tokens disponibles.

|nombre|Descripción|
|----------|-----------------|
|$SharePoint.Project.FileName$|El nombre de la que contiene, como archivo de proyecto *contenedor*.|
|$SharePoint.Project.FileNameWithoutExtension$|El nombre del archivo del proyecto que contiene sin la extensión de nombre de archivo. Por ejemplo, "NuevoProy".|
|$SharePoint.Project.AssemblyFullName$|El nombre para mostrar del proyecto contenedor (nombre seguro) del ensamblado de salida.|
|$SharePoint.Project.AssemblyFileName$|Nombre del proyecto contenedor de salida del ensamblado.|
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Nombre del proyecto contenedor de salida del ensamblado sin la extensión de nombre de archivo.|
|$SharePoint.Project.AssemblyPublicKeyToken$|Del proyecto que contiene el token de clave pública del ensamblado de salida, puede convertida en una cadena. (16 caracteres en "x2" formato hexadecimal.)|
|$SharePoint.Package.Name$|El nombre del paquete que lo contiene.|
|$SharePoint.Package.FileName$|El nombre del archivo de definición del paquete contenedor.|
|$SharePoint.Package.FileNameWithoutExtension$|El nombre del archivo de definición del paquete contenedor (sin extensión).|
|$SharePoint.Package.Id$|Id. de SharePoint para el paquete contenedor. Si se usa una característica en más de un paquete, este valor cambiará.|
|$SharePoint.Feature.FileName$|El nombre del archivo de definición de la que contiene la característica, como *Feature1.feature*.|
|$SharePoint.Feature.FileNameWithoutExtension$|El nombre del archivo de definición de función, sin la extensión de nombre de archivo.|
|$SharePoint.Feature.DeploymentPath$|El nombre de la carpeta que contiene la característica en el paquete. Este token equivale a la propiedad "Ruta de acceso de implementación" en el Diseñador de características. Un valor de ejemplo es, "Project1_Feature1".|
|$SharePoint.Feature.Id$|Id. de SharePoint de la característica. Este token, como con todos los tokens de nivel de característica, se pueden usar únicamente por los archivos incluidos en un paquete a través de una característica, no agrega directamente a un paquete fuera de una característica.|
|$SharePoint.ProjectItem.Name$|El nombre del elemento de proyecto (no su nombre de archivo), obtenido de **ISharePointProjectItem.Name**.|
|$SharePoint.Type.\<GUID>.AssemblyQualifiedName$|El nombre completo del ensamblado de la coincidencia de tipo el [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] del token. El formato de la [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] está en minúsculas y se corresponde con el formato de GUID.ToString (es decir, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|
|$SharePoint.Type.\<GUID>.FullName$|El nombre completo del tipo de coincidencia de GUID en el token. El formato del GUID en minúsculas y se corresponde con el formato de GUID.ToString (es decir, xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx).|

## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Agregar extensiones a la lista de extensiones de archivo de reemplazo de tokens
 Aunque, en teoría, se pueden usar tokens en cualquier archivo que pertenece a un proyecto de SharePoint incluido elementos en el paquete, de forma predeterminada, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] busca tokens solo en los archivos de paquete, los archivos de manifiesto y los archivos que tienen las siguientes extensiones:

- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]

- ASCX

- ASPX

- Elemento Web

- DWP

  Estas extensiones se definen mediante la `<TokenReplacementFileExtensions>` elemento en el archivo Microsoft.VisualStudio.SharePoint.targets, ubicado en el... \\< archivos de programa\>\MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools carpeta.

  Sin embargo, puede agregar extensiones de archivo adicionales a la lista. Agregar un `<TokenReplacementFileExtensions>` elemento a cualquier elemento PropertyGroup en el archivo de proyecto de SharePoint que se define antes de la \<Import > del archivo de destinos de SharePoint.

> [!NOTE]
>  Como reemplazo de tokens se produce una vez compilado un proyecto, no debe agregar extensiones de archivo para tipos de archivo que se compilan, tales como *.cs*, *.vb* o *.resx*. Los tokens se reemplazan sólo en los archivos que no se compilan.

 Por ejemplo, para agregar las extensiones de nombre de archivo (*.myextension* y *.yourextension*) a la lista de extensiones de nombre de archivo de reemplazo de tokens, se debe agregar lo siguiente a un proyecto (*.csproj* ) archivo:

```xml
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

 Puede agregar la extensión directamente a los destinos (*.targets*) archivo. Sin embargo, agregar la extensión modifica la lista de extensiones para todos los proyectos de SharePoint que se empaquetan en el sistema local, no solo su propia. Esta extensión puede ser conveniente cuando usted es el único desarrollador en el sistema o si así lo requiere la mayoría de los proyectos. Sin embargo, dado que es específica del sistema, este enfoque no es portable y, por lo tanto, se recomienda que se agregar todas las extensiones al archivo de proyecto en su lugar.

## <a name="see-also"></a>Vea también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
