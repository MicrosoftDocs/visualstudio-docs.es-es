---
title: "SignFile (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#SignFile"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, SignFile (tarea)"
  - "SignFile (tarea) [MSBuild]"
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# SignFile (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Firma un archivo determinado con el certificado especificado.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `SignFile`.  
  
 Tenga en cuenta que los certificados SHA\-256 solo están permitidos en equipos que tienen .NET 4.5 y versiones posteriores.  
  
> [!WARNING]
>  A partir de Visual Studio 2013 Update 3, esta tarea tiene una signatura nueva que le permite especificar la versión del marco de trabajo de destino para el archivo.  Le recomendamos utilizar la nueva firma, siempre que sea posible, ya que el proceso de MSBuild solo utiliza hashes SHA\-256 cuando el marco de trabajo de destino es .NET 4.5 o una versión posterior.  Si el marco de trabajo destino es .NET 4.0 o una versión anterior, no se utilizará el hash SHA\-256.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`CertificateThumbprint`|Parámetro `String` requerido.<br /><br /> Especifica el certificado que se va a usar en la signatura.  Este certificado debe estar ubicado en el almacén personal del usuario actual.|  
|`SigningTarget`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica los archivos que se van a firmar con el certificado.|  
|`TimestampUrl`|Parámetro `String` opcional.<br /><br /> Especifica la dirección URL del servidor con marca de tiempo.|  
|`TargetFrameworkVersion`|La versión de .NET Framework la que se utiliza para el destino.|  
  
## Comentarios  
 Además de los parámetros enumerados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [Task Base \(Clase\)](../msbuild/task-base-class.md).  
  
## Ejemplo  
 En el ejemplo siguiente se utiliza la tarea `SignFile` para firmar los archivos especificados en la colección de elementos `FilesToSign` con el certificado definido por la propiedad `Certificate`.  
  
```  
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
>  La huella digital del certificado es el hash SHA\-1 del certificado.  Para obtener más información, consulte el artículo sobre cómo [obtener el hash SHA\-1 de un certificado de entidad de certificación raíz de confianza](http://msdn.microsoft.com/es-es/dd641990-9a88-4228-a245-017797131a87).  
  
## Ejemplo  
 En el ejemplo siguiente se utiliza la tarea `Exec` para firmar los archivos especificados en la colección de elementos `FilesToSign` con el certificado definido por la propiedad `Certificate`.  Puede utilizar esto para firmar archivos de Windows Installer durante el proceso de generación.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.msi" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <Exec Command="signtool.exe sign /f CertFile /p Password "@(FileToSign)" "/>  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.0" />  
    </Target>  
</Project>  
```  
  
## Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Tareas](../msbuild/msbuild-tasks.md)