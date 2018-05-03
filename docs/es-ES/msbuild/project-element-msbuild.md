---
title: Elemento Project (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44f63cf4517320b9acea0d289723a511dfeb9570
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="project-element-msbuild"></a>Elemento Project (MSBuild)
Elemento raíz necesario de un archivo de proyecto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .  

## <a name="syntax"></a>Sintaxis  

```  
<Project InitialTargets="TargetA;TargetB"  
         DefaultTargets="TargetC;TargetD"  
         TreatAsLocalProperty="PropertyA;PropertyB"  
         ToolsVersion=<version number>
         Sdk="name[/version]"
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Sdk... />
    <Choose>... </Choose>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Target>... </Target>  
    <UsingTask.../>  
    <ProjectExtensions>... </ProjectExtensions>  
    <Import... />  
</Project>  
```  

## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  

### <a name="attributes"></a>Atributos  

|Atributo|Description|  
|---------------|-----------------|  
|`DefaultTargets`|Atributo opcional.<br /><br /> Destinos predeterminados que serán el punto de entrada de la compilación si no se ha especificado ningún destino. Si hay varios destinos, se delimitan con punto y coma (;).<br /><br /> Si no se especifica ningún destino predeterminado ni en el atributo `DefaultTargets` ni en la línea de comandos de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], el motor ejecuta el primer destino en el archivo del proyecto una vez evaluados los elementos [Import](../msbuild/import-element-msbuild.md).|  
|`InitialTargets`|Atributo opcional.<br /><br /> Destinos iniciales que se van a ejecutar antes que los destinos especificados en el atributo `DefaultTargets` o en la línea de comandos. Si hay varios destinos, se delimitan con punto y coma (;).|  
|`Sdk`|Atributo opcional. <br /><br /> El nombre del SDK y la versión opcional se usa para crear instrucciones Import implícitas que se agregan al archivo .proj. Si no se especifica ninguna versión, MSBuild intentará resolver una versión predeterminada.  Por ejemplo: `<Project Sdk="Microsoft.NET.Sdk" />` o `<Project Sdk="My.Custom.Sdk/1.0.0" />`.|  
|`ToolsVersion`|Atributo opcional.<br /><br /> La versión del conjunto de herramientas de MSBuild que se utiliza para determinar los valores de $(MSBuildBinPath) y $(MSBuildToolsPath).|  
|`TreatAsLocalProperty`|Atributo opcional.<br /><br /> Nombres de propiedad que no se consideran globales. Este atributo impide que determinadas propiedades de la línea de comandos invaliden los valores de propiedad que se establecen en un archivo del proyecto o de destinos y todas las importaciones posteriores. Si hay varias propiedades, se delimitan con punto y coma (;).<br /><br /> Normalmente, las propiedades globales invalidan los valores de propiedad que se establecen en el archivo del proyecto o de destinos. Si la propiedad aparece en el valor `TreatAsLocalProperty`, el valor de propiedad global no invalida los valores de propiedad que se establecen en ese archivo ni las importaciones posteriores. Para obtener más información, consulte [Cómo: Compilar los mismos archivos de origen con diferentes opciones](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Nota:** Establezca propiedades globales en el símbolo del sistema mediante el modificador **/property** (o **/p**). También puede establecer o modificar propiedades globales para proyectos secundarios en una compilación de varios proyectos mediante el atributo `Properties` de la tarea de MSBuild. Para obtener más información, consulte [Tarea de MSBuild](../msbuild/msbuild-task.md).|  
|`Xmlns`|Atributo opcional.<br /><br /> Cuando se especifica, el atributo `xmlns` debe tener el valor de "http://schemas.microsoft.com/developer/msbuild/2003".|  

### <a name="child-elements"></a>Elementos secundarios  

|Elemento|Description|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Elemento opcional.<br /><br /> Evalúa los elementos secundarios para seleccionar un conjunto de elementos `ItemGroup` o `PropertyGroup` para evaluar.|  
|[Import](../msbuild/import-element-msbuild.md)|Elemento opcional.<br /><br /> Permite a un archivo del proyecto importar otro archivo del proyecto. Puede haber cero o más elementos `Import` en un proyecto.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Elemento opcional.<br /><br /> Un elemento de agrupamiento para elementos individuales. Los elementos se especifican mediante el elemento [Item](../msbuild/item-element-msbuild.md). Puede haber cero o más elementos `ItemGroup` en un proyecto.|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|Elemento opcional.<br /><br /> Proporciona una manera de conservar información no relativa a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] en un archivo del proyecto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Puede haber cero o un elementos `ProjectExtensions` en un proyecto.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Elemento opcional.<br /><br /> Un elemento de agrupamiento para propiedades individuales. Las propiedades se especifican mediante el elemento [Property](../msbuild/property-element-msbuild.md). Puede haber cero o más elementos `PropertyGroup` en un proyecto.|
|[Sdk](../msbuild/sdk-element-msbuild.md)|Elemento opcional.<br /><br /> Hace referencia a un SDK de proyecto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Este elemento se puede usar como alternativa para el atributo Sdk.|  
|[Target](../msbuild/target-element-msbuild.md)|Elemento opcional.<br /><br /> Contiene un conjunto de tareas para que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] las ejecute de manera secuencial. Las tareas se especifican mediante el elemento [Task](../msbuild/task-element-msbuild.md). Puede haber cero o más elementos `Target` en un proyecto.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Elemento opcional.<br /><br /> Proporciona una manera de registrar las tareas en [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Puede haber cero o más elementos `UsingTask` en un proyecto.|  

### <a name="parent-elements"></a>Elementos primarios  
 Ninguno.  

## <a name="see-also"></a>Vea también  
 [Cómo: Especificar qué destino utilizar primero al compilar](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)   
 [Referencia de esquemas de archivo del proyecto](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)
