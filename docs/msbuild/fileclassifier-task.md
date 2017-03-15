---
title: FileClassifier (Tarea) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
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
caps.latest.revision: 7
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 72461ba86f447aa2caed09409fe3f26f475f57b5
ms.lasthandoff: 02/22/2017

---
# <a name="fileclassifier-task"></a>FileClassifier (Tarea)
La tarea <xref:Microsoft.Build.Tasks.Windows.FileClassifier> clasifica un conjunto de recursos de código fuente como los que se van a incrustar en un ensamblado. Si un recurso no es localizable, se incrusta en el ensamblado de aplicación principal; de lo contrario, se incrusta en un ensamblado satélite.  
  
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
  
```xml  
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
 [Compilar una aplicación de WPF (WPF)](http://msdn.microsoft.com/Library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
