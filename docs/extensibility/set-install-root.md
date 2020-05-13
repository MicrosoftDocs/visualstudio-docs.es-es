---
title: Instalación fuera de la carpeta de extensiones con VSIX v3 Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa2c7d97dda9bba139ec613b367eedbc6307848a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700181"
---
# <a name="install-outside-the-extensions-folder"></a>Instalar fuera de la carpeta de extensiones

A partir de Visual Studio 2017 y VSIX v3 (versión 3), los activos de extensión se pueden instalar fuera de la carpeta de extensiones. Actualmente, las siguientes ubicaciones están habilitadas como ubicaciones de instalación válidas (donde [INSTALLDIR] se asigna al directorio de instalación de la instancia de Visual Studio):

* [INSTALLDIR]-MSBuild
* [INSTALLDIR]-Xml-Schemas
* [INSTALLDIR]-Common7-IDE-PublicAssemblies
* [INSTALLDIR]-Licencias
* [INSTALLDIR]-Common7-IDE-ReferenceAssemblies
* [INSTALLDIR]-Common7-IDE-RemoteDebugger
* [INSTALLDIR]-Common7-IDE-VC-VCTargets (solo se admite para Visual Studio 2017; en desuso para Visual Studio 2019 y versiones posteriores)

> [!NOTE]
> El formato VSIX no permite instalar fuera de la estructura de carpetas de instalación de Visual Studio. 

Para admitir la instalación en estos directorios, el VSIX debe instalarse "por instancia por máquina". Esto se puede habilitar marcando la casilla de verificación "todos los usuarios" en el diseñador extension.vsixmanifest:

![comprobar todos los usuarios](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>Cómo configurar InstallRoot

Para establecer los directorios de instalación, puede usar la ventana **Propiedades** en Visual Studio. Por ejemplo, puede `InstallRoot` establecer la propiedad de una referencia de proyecto a una de las ubicaciones anteriores:

![instalar propiedades raíz](media/install-root-properties.png)

Esto agregará algunos metadatos `ProjectReference` a la propiedad correspondiente dentro del archivo .csproj del proyecto VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> Puede editar el archivo .csproj directamente, si lo prefiere.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>Cómo establecer una subruta en InstallRoot

Si desea instalar en una subruta `InstallRoot`debajo de la , `VsixSubPath` puede hacerlo `InstallRoot` estableciendo la propiedad al igual que la propiedad. Por ejemplo, supongamos que queremos que la salida de nuestra referencia de proyecto se instale en '[INSTALLDIR], MSBuild, MyCompany, MySDK, 1.0'. Podemos hacerlo fácilmente con el diseñador de propiedades:

![establecer subtrayecto](media/set-subpath.png)

Los cambios .csproj correspondientes tendrán este aspecto:

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>Información adicional

Los cambios del diseñador de propiedades se aplican a algo más que referencias de proyecto; también puede `InstallRoot` establecer los metadatos de los elementos dentro del proyecto (utilizando los mismos métodos descritos anteriormente).
