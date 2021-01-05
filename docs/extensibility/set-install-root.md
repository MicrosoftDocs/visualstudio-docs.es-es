---
title: Instalación fuera de la carpeta de extensiones con VSIX V3 | Microsoft Docs
description: Obtenga información sobre cómo instalar recursos de extensión del SDK de Visual Studio fuera de la carpeta extensiones y qué ubicaciones son válidas.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 73bfb963122762c3185a964826a11dca5e771717
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2020
ms.locfileid: "97716021"
---
# <a name="install-outside-the-extensions-folder"></a>Instalar fuera de la carpeta de extensiones

A partir de Visual Studio 2017 y VSIX V3 (versión 3), los recursos de extensión se pueden instalar fuera de la carpeta de extensiones. Actualmente, las siguientes ubicaciones están habilitadas como ubicaciones de instalación válidas (donde [INSTALLDIR] está asignada al directorio de instalación de la instancia de Visual Studio):

* [INSTALLDIR] \MSBuild
* [INSTALLDIR] \Xml\Schemas
* [INSTALLDIR] \Common7\IDE\PublicAssemblies
* [INSTALLDIR] \Licenses
* [INSTALLDIR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDIR] \Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets (solo se admite para Visual Studio 2017; desusado para Visual Studio 2019 y versiones posteriores)

> [!NOTE]
> El formato VSIX no permite instalar fuera de la estructura de carpetas de instalación de Visual Studio. 

Para admitir la instalación en estos directorios, VSIX debe estar instalado "por instancia por equipo". Para habilitarlo, active la casilla "todos los usuarios" en el diseñador de extension. vsixmanifest:

![comprobar todos los usuarios](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Cómo establecer el valor de InstallRoot

Para establecer los directorios de instalación, puede usar la ventana **propiedades** de Visual Studio. Por ejemplo, puede establecer la `InstallRoot` propiedad de una referencia de proyecto en una de las ubicaciones anteriores:

![propiedades de la raíz de instalación](media/install-root-properties.png)

Esto agregará algunos metadatos a la `ProjectReference` propiedad correspondiente dentro del archivo. csproj del Proyecto VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Puede editar el archivo. csproj directamente, si lo prefiere.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Cómo establecer un subtrazado en el InstallRoot

Si desea realizar la instalación en un subtrazado bajo `InstallRoot` , puede hacerlo estableciendo la `VsixSubPath` propiedad como la `InstallRoot` propiedad. Por ejemplo, supongamos que queremos que la salida de la referencia del proyecto se instale en ' [INSTALLDIR] \MSBuild\MyCompany\MySDK\1.0 '. Esto se puede hacer fácilmente con el diseñador de propiedades:

![establecer subtrazado](media/set-subpath.png)

Los cambios de. csproj correspondientes tendrán el siguiente aspecto:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Información adicional

Los cambios del diseñador de propiedades se aplican a más que solo las referencias del proyecto; también puede establecer los `InstallRoot` metadatos de los elementos dentro del proyecto (con los mismos métodos descritos anteriormente).
