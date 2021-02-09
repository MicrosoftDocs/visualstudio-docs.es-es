---
title: Parámetros reemplazables | Microsoft Docs
description: Revise los parámetros reemplazables (tokens), que especifican valores dentro de los archivos de proyecto para los elementos de la solución de SharePoint cuyos valores reales no se conocen en tiempo de diseño.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload: office
ms.openlocfilehash: 3eb6e737a1f939e05e6a6be7f2c9ba950fc411d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889504"
---
# <a name="replaceable-parameters"></a>Parámetros reemplazables
  Los parámetros reemplazables, o *tokens*, se pueden usar dentro de los archivos de proyecto para proporcionar valores para los elementos de la solución de SharePoint cuyos valores reales no se conocen en tiempo de diseño. Son similares en función de los [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tokens de plantilla estándar. Para obtener más información, vea [parámetros de plantilla](../ide/template-parameters.md).

## <a name="token-format"></a>Formato de tokens
 Los tokens comienzan y terminan con un carácter de signo de dólar ($). En la implementación, los tokens utilizados se reemplazan por valores reales cuando un proyecto se empaqueta en un paquete de solución de SharePoint (archivo *. wsp* ). Por ejemplo, el token **$SharePoint. Package.Name $** podría resolverse como la cadena "paquete de SharePoint de prueba".

## <a name="token-rules"></a>Reglas de token
 Las siguientes reglas se aplican a los tokens:

- Los tokens se pueden especificar en cualquier parte de una línea.

- Los tokens no pueden abarcar varias líneas.

- El mismo token se puede especificar más de una vez en la misma línea y en el mismo archivo.

- Pueden especificarse tokens diferentes en la misma línea.

  Los tokens que no siguen estas reglas se omiten y no dan como resultado una advertencia o un error.

  La sustitución de tokens por valores de cadena se realiza inmediatamente después de la transformación del manifiesto. Este reemplazo permite al usuario editar las plantillas de manifiesto con tokens.

### <a name="token-name-resolution"></a>Resolución de nombres de token
 En la mayoría de los casos, un token se resuelve en un valor específico, independientemente de dónde se encuentre. Sin embargo, si el token está relacionado con un paquete o característica, el valor del token depende de dónde se encuentre. Por ejemplo, si una característica está en el paquete A, el token se `$SharePoint.Package.Name$` resuelve en el valor "paquete a". Si la misma característica está en el paquete B, se `$SharePoint.Package.Name$` resuelve como "paquete b".

## <a name="tokens-list"></a>Lista de tokens
 En la tabla siguiente se enumeran los tokens disponibles.

|Nombre|Descripción|
|----------|-----------------|
|$SharePoint. Project. FileName $|Nombre del archivo de proyecto que lo contiene, como, por ejemplo, *NewProj. csproj*.|
|$SharePoint. Project. Nombredearchivosinextensión $|Nombre del archivo de proyecto contenedor sin la extensión de nombre de archivo. Por ejemplo, "NewProj".|
|$SharePoint. Project. AssemblyFullName $|Nombre para mostrar (nombre seguro) del ensamblado de salida del proyecto contenedor.|
|$SharePoint. Project. AssemblyFileName $|Nombre del ensamblado de salida del proyecto contenedor.|
|$SharePoint. Project. AssemblyFileNameWithoutExtension $|Nombre del ensamblado de salida del proyecto contenedor, sin la extensión de nombre de archivo.|
|$SharePoint. Project. AssemblyPublicKeyToken $|Token de clave pública del ensamblado de salida del proyecto contenedor, convertido en una cadena. (16 caracteres en formato hexadecimal "x2").|
|$SharePoint. Package.Name $|Nombre del paquete contenedor.|
|$SharePoint. Package. FileName $|Nombre del archivo de definición del paquete contenedor.|
|$SharePoint. Package. Nombredearchivosinextensión $|Nombre (sin extensión) del archivo de definición del paquete contenedor.|
|$SharePoint. Package.Id $|El identificador de SharePoint para el paquete contenedor. Si una característica se utiliza en más de un paquete, este valor cambiará.|
|$SharePoint. Feature. FileName $|Nombre del archivo de definición de la característica que lo contiene, como *Feature1. Feature*.|
|$SharePoint. Feature. Nombredearchivosinextensión $|Nombre del archivo de definición de características, sin la extensión de nombre de archivo.|
|$SharePoint. Feature. DeploymentPath $|El nombre de la carpeta que contiene la característica en el paquete. Este token equivale a la propiedad "ruta de acceso de implementación" en el diseñador de características. Un valor de ejemplo es, "Project1_Feature1".|
|$SharePoint. Feature.Id $|El identificador de SharePoint de la característica que lo contiene. Este token, al igual que con todos los tokens de nivel de característica, solo se puede usar en los archivos incluidos en un paquete a través de una característica, no se agrega directamente a un paquete fuera de una característica.|
|$SharePoint. ProjectItem.Name $|Nombre del elemento de proyecto (no su nombre de archivo), tal y como se obtiene de **ISharePointProjectItem.Name**.|
|$SharePoint. Type. \<GUID> . AssemblyQualifiedName $|Nombre calificado con el ensamblado del tipo que coincide con el [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] del token. El formato de [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] es en minúsculas y corresponde al formato GUID. ToString ("D") (es decir, xxxxxxxx-XXXX-XXXX-XXXX-XXXXXXXXXXXX).|
|$SharePoint. Type. \<GUID> . FullName $|Nombre completo del tipo que coincide con el GUID en el token. El formato del GUID es en minúsculas y corresponde al formato GUID. ToString ("D") (es decir, xxxxxxxx-XXXX-XXXX-XXXX-XXXXXXXXXXXX).|

## <a name="add-extensions-to-the-token-replacement-file-extensions-list"></a>Agregar extensiones a la lista de extensiones de archivo de reemplazo de token
 Aunque los tokens pueden ser utilizados teóricamente por cualquier archivo que pertenezca a un elemento de proyecto de SharePoint incluido en el paquete, de forma predeterminada [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] busca tokens únicamente en archivos de paquete, archivos de manifiesto y archivos con las siguientes extensiones:

- [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]

- ASCX

- ASPX

- WebPart

- DWP

  Estas extensiones se definen mediante el `<TokenReplacementFileExtensions>` elemento en el archivo Microsoft. VisualStudio. SharePoint. targets, que se encuentra en la carpeta... \\<archivos de programa \> \MSBuild\Microsoft\VisualStudio\v11.0\SharePointTools.

  Sin embargo, puede Agregar extensiones de archivo adicionales a la lista. Agregue un `<TokenReplacementFileExtensions>` elemento a cualquier propertyGroup en el archivo de proyecto de SharePoint que se define antes del \<Import> archivo de destinos de SharePoint.

> [!NOTE]
> Dado que el reemplazo de tokens se produce después de la compilación de un proyecto, no debe agregar extensiones de archivo para los tipos de archivo que se compilan, como *. CS*, *. VB* o *. resx*. Los tokens solo se reemplazan en archivos que no están compilados.

 Por ejemplo, para agregar las extensiones de nombre de archivo (*.* *yourextension*) a la lista de extensiones de nombre de archivo de reemplazo de token, debe agregar lo siguiente a un archivo de proyecto (*. csproj*):

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

 Puede Agregar la extensión directamente al archivo de destinos (*. targets*). Sin embargo, al agregar la extensión, se modifica la lista de extensiones para todos los proyectos de SharePoint empaquetados en el sistema local, no solo en el suyo propio. Esta extensión puede ser útil cuando usted es el único desarrollador del sistema o si la mayoría de los proyectos lo requieren. Sin embargo, dado que es específico del sistema, este enfoque no es portátil y, por lo tanto, se recomienda que agregue las extensiones al archivo de proyecto en su lugar.

## <a name="see-also"></a>Consulte también
- [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)
