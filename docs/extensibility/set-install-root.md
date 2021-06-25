---
title: Instalación fuera de la carpeta extensions con VSIX v3 | Microsoft Docs
description: Obtenga información sobre cómo Visual Studio recursos de extensión del SDK fuera de la carpeta de extensiones y qué ubicaciones son válidas.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 24b1e1a73ff588e5531eec2025c8a3c9e94760a4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898453"
---
# <a name="install-outside-the-extensions-folder"></a>Instalar fuera de la carpeta de extensiones

A partir Visual Studio 2017 y VSIX v3 (versión 3), los recursos de extensión se pueden instalar fuera de la carpeta de extensiones. Actualmente, las siguientes ubicaciones están habilitadas como ubicaciones de instalación válidas (donde [INSTALLDIR] se asigna al directorio de instalación de la Visual Studio de instalación de la instancia):

* [INSTALLDIR]\MSBuild
* [INSTALLDIR]\Xml\Schemas
* [INSTALLDIR]\Common7\IDE\PublicAssemblies
* [INSTALLDIR]\Licenses
* [INSTALLDIR]\Common7\IDE\ReferenceAssemblies
* [INSTALLDIR]\Common7\IDE\RemoteDebugger
* [INSTALLDIR]\Common7\IDE\VC\VCTargets (solo se admite para Visual Studio 2017; está en desuso para Visual Studio 2019 y versiones posteriores)

> [!NOTE]
> El formato VSIX no le permite instalar fuera de la estructura Visual Studio carpeta de instalación. 

Para admitir la instalación en estos directorios, el VSIX debe instalarse "por instancia por equipo". Esto se puede habilitar activando la casilla "todos los usuarios" en el diseñador extension.vsixmanifest:

![comprobar todos los usuarios](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Cómo establecer InstallRoot

Para establecer los directorios de instalación, puede usar la **ventana Propiedades** de Visual Studio. Por ejemplo, puede establecer la propiedad `InstallRoot` de una referencia de proyecto en una de las ubicaciones anteriores:

![instalar propiedades raíz](media/install-root-properties.png)

Esto agregará algunos metadatos a la propiedad correspondiente dentro del archivo `ProjectReference` .csproj del proyecto VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Puede editar el archivo .csproj directamente, si lo prefiere.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Cómo establecer una sub ruta de acceso en InstallRoot

Si desea instalar en una sub ruta de acceso debajo de , puede hacerlo estableciendo la `InstallRoot` propiedad igual que la propiedad `VsixSubPath` `InstallRoot` . Por ejemplo, digamos que queremos que la salida de la referencia del proyecto se instale en "[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0". Podemos hacerlo fácilmente con el diseñador de propiedades:

![set subpath](media/set-subpath.png)

Los cambios .csproj correspondientes tendrán el siguiente aspecto:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Información adicional

Los cambios del diseñador de propiedades se aplican a algo más que a referencias de proyecto; También puede establecer los metadatos de los elementos dentro `InstallRoot` del proyecto (con los mismos métodos descritos anteriormente).
