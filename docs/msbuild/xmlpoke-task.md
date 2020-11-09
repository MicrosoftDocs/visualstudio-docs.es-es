---
title: XmlPoke (Tarea) | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa la tarea XmlPoke para establecer los valores especificados por una consulta XPath en un archivo XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35e29004116807092452a08d3835ba3e5e1dabcd
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047234"
---
# <a name="xmlpoke-task"></a>XmlPoke (tarea)

Establece los valores especificados por una consulta XPath en un archivo XML.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `XmlPoke` .

|Parámetro|Description|
|---------------|-----------------|
|`Namespaces`|Parámetro `String` opcional.<br /><br /> Especifica los espacios de nombres para los prefijos de la consulta XPath. `Namespaces` es un fragmento XML que consta de elementos `Namespace` con los atributos `Prefix` y `Uri`. El atributo `Prefix` especifica el prefijo para asociar con el espacio de nombres especificado en el atributo `Uri`. No use un valor `Prefix` vacío.|
|`Query`|Parámetro `String` opcional.<br /><br /> Especifica la consulta XPath.|
|`Value`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica el valor que se va a insertar en la ruta de acceso especificada.|
|`XmlInputPath`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica la entrada XML como una ruta de acceso a archivo.|

## <a name="remarks"></a>Comentarios

 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Ejemplo

Puede modificar este archivo de ejemplo sample.xml:

```xml
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

En este ejemplo, si quiere modificar `/Package/mp:PhoneIdentity/PhoneProductId`, use lo siguiente:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Namespace>
        <Namespace Prefix="dn" Uri="http://schemas.microsoft.com/appx/manifest/foundation/windows10" />
        <Namespace Prefix="mp" Uri="http://schemas.microsoft.com/appx/2014/phone/manifest" />
        <Namespace Prefix="uap" Uri="http://schemas.microsoft.com/appx/manifest/uap/windows10" />
    </Namespace>
</PropertyGroup>

<Target Name="Poke">
  <XmlPoke
    XmlInputPath="Sample.xml"
    Value="MyId"
    Query="/dn:Package/mp:PhoneIdentity/@PhoneProductId"
    Namespaces="$(Namespace)"/>
</Target>
</Project>
```

`dn` aquí se usa como un prefijo de espacio de nombres artificial para el espacio de nombres predeterminado.

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
