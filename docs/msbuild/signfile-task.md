---
title: Tarea SignFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 329cef79c529850bbe90a62cc24d5ec989379aa9
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="signfile-task"></a>SignFile (Tarea)

Firma un archivo determinado con el certificado especificado.
  
## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `SignFile`.
  
 Tenga en cuenta que los certificados SHA-256 solo están permitidos en equipos que tienen .NET 4.5 y versiones posteriores.
  
> [!WARNING]
> A partir de Visual Studio 2013 Update 3, esta tarea tiene una signatura nueva que le permite especificar la versión de la plataforma de destino para el archivo. Le recomendamos utilizar la nueva firma, siempre que sea posible, ya que el proceso de MSBuild solo utiliza hashes SHA-256 cuando la plataforma de destino es .NET 4.5 o una versión posterior. Si la plataforma de destino es .NET 4.0 o una versión anterior, no se utilizará el hash SHA-256.
  
|Parámetro|Description|
|---------------|-----------------|
|`CertificateThumbprint`|Parámetro `String` requerido.<br /><br /> Especifica el certificado que se va a usar en la signatura. Este certificado debe estar ubicado en el almacén personal del usuario actual.|
|`SigningTarget`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica los archivos que se van a firmar con el certificado.|
|`TimestampUrl`|Parámetro `String` opcional.<br /><br /> Especifica la dirección URL del servidor con marca de tiempo.|
|`TargetFrameworkVersion`|La versión de .NET Framework la que se utiliza para el destino.|
  
## <a name="remarks"></a>Comentarios

 Además de los parámetros enumerados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [Task Base (Clase)](../msbuild/task-base-class.md).
  
## <a name="example"></a>Ejemplo

 En el ejemplo siguiente se utiliza la tarea `SignFile` para firmar los archivos especificados en la colección de elementos `FilesToSign` con el certificado definido por la propiedad `Certificate`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <FileToSign Include="File.exe" />
    </ItemGroup>
    <PropertyGroup>
        <Certificate>Cert.cer</Certificate>
    </PropertyGroup>
    <Target Name="Sign">
        <SignFile
            CertificateThumbprint="$(CertificateThumbprint)"
            SigningTarget="@(FileToSign)"
            TargetFrameworkVersion="v4.5" />
    </Target>
</Project>
```

> [!NOTE]
> La huella digital del certificado es el hash SHA-1 del certificado. Para obtener más información, vea el artículo sobre cómo [obtener el hash SHA-1 de un certificado de entidad de certificación raíz de confianza](http://msdn.microsoft.com/en-us/dd641990-9a88-4228-a245-017797131a87).
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Tareas](../msbuild/msbuild-tasks.md)