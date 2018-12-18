---
title: FileClassifier (Tarea) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- classifying a resource set to embed in an assembly [WPF MSBuild]
- non-localizable resources [WPF MSBuild], classifying to embed in an assembly
- FileClassifier task [WPF MSBuild]
ms.assetid: 14e03310-fcc0-4bb2-a84d-cda12be66367
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e0515d4f21993a50ce590df10ca283e6e66b17a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271448"
---
# <a name="fileclassifier-task"></a>FileClassifier (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
La tarea <xref:Microsoft.Build.Tasks.Windows.FileClassifier> clasifica un conjunto de recursos de origen como los que se insertarán en un ensamblado. Si un recurso no es localizable, se incrusta en el ensamblado de aplicación principal; de lo contrario, se incrusta en un ensamblado satélite.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`CLREmbeddedResource`|Sin usar.|  
|`CLRResourceFiles`|Sin usar.|  
|`CLRSatelliteEmbeddedResource`|Sin usar.|  
|`Culture`|Parámetro **String** opcional.<br /><br /> Especifica la referencia cultural de la compilación. Este valor puede ser **null** si la compilación no es localizable. Sies **null**, se usa de forma predeterminada el valor en minúscula que devuelve **CultureInfo.InvariantCulture**.|  
|`MainEmbeddedFiles`|Parámetro de salida opcional de tipo **ITaskItem[]**.<br /><br /> Especifica los recursos no localizables que se insertan en el ensamblado principal.|  
|`OutputType`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica el tipo de archivo en el que se van a insertar los archivos de origen especificados. Los valores válidos son **exe**, **winexe** o **library**.|  
|`SatelliteEmbeddedFiles`|Parámetro de salida opcional de tipo **ITaskItem[]**.<br /><br /> Especifica los archivos localizables que se insertan en el ensamblado satélite para la referencia cultural especificada en el parámetro **Culture**.|  
|`SourceFiles`|Parámetro obligatorio de tipo **ITaskItem[]**.<br /><br /> Especifica la lista de archivos que se van a clasificar.|  
  
## <a name="remarks"></a>Comentarios  
 Si no se establece el valor del parámetro **Culture**, todos los recursos que especifica el parámetro **SourceFiles** no son localizables; de lo contrario, son localizables, a menos que se asocien a un atributo **Localizable** cuyo valor se establezca en **false**.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se clasifica un archivo origen como recurso y, a continuación, se inserta en un ensamblado satélite para la referencia cultural Francés canadiense (fr-CA).  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.FileClassifier"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <ItemGroup>  
    <Resource Include="Resource1.bmp" />  
  </ItemGroup>  
  <Target Name="FileClassifierTask">  
    <FileClassifier  
      SourceFiles="Resource1.bmp"  
      Culture="fr-CA"  
      OutputType="exe" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Compilar una aplicación de WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)



