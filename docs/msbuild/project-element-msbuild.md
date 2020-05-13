---
title: Elemento Project (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df9eff3e941cc21aaa71c2779a72084e12e8e590
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632984"
---
# <a name="project-element-msbuild"></a>Elemento Project (MSBuild)

Elemento raíz necesario de un archivo de proyecto de MSBuild.

## <a name="syntax"></a>Sintaxis

```xml
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

| Atributo | Descripción |
|------------------------| - |
| `DefaultTargets` | Atributo opcional.<br /><br /> Destinos predeterminados que serán el punto de entrada de la compilación si no se ha especificado ningún destino. Si hay varios destinos, se delimitan con punto y coma (;).<br /><br /> Si no se especifica ningún destino predeterminado ni en el atributo `DefaultTargets` ni en la línea de comandos de MSBuild, el motor ejecuta el primer destino en el archivo del proyecto una vez evaluados los elementos [Import](../msbuild/import-element-msbuild.md). |
| `InitialTargets` | Atributo opcional.<br /><br /> Destinos iniciales que se van a ejecutar antes que los destinos especificados en el atributo `DefaultTargets` o en la línea de comandos. Si hay varios destinos, se delimitan con punto y coma (`;`). Si varios archivos importados definen `InitialTargets`, se ejecutarán todos los destinos que se han mencionado, en el orden en el que se encuentran las importaciones. |
| `Sdk` | Atributo opcional. <br /><br /> El nombre del SDK y la versión opcional se usa para crear instrucciones Import implícitas que se agregan al archivo .proj. Si no se especifica ninguna versión, MSBuild intentará resolver una versión predeterminada.  Por ejemplo: `<Project Sdk="Microsoft.NET.Sdk" />` o `<Project Sdk="My.Custom.Sdk/1.0.0" />`. |
| `ToolsVersion` | Atributo opcional.<br /><br /> La versión del conjunto de herramientas de MSBuild que se utiliza para determinar los valores de $(MSBuildBinPath) y $(MSBuildToolsPath). |
| `TreatAsLocalProperty` | Atributo opcional.<br /><br /> Nombres de propiedad que no se consideran globales. Este atributo impide que determinadas propiedades de la línea de comandos invaliden los valores de propiedad que se establecen en un archivo del proyecto o de destinos y todas las importaciones posteriores. Si hay varias propiedades, se delimitan con punto y coma (;).<br /><br /> Normalmente, las propiedades globales invalidan los valores de propiedad que se establecen en el archivo del proyecto o de destinos. Si la propiedad aparece en el valor `TreatAsLocalProperty`, el valor de propiedad global no invalida los valores de propiedad que se establecen en ese archivo ni las importaciones posteriores. Para obtener más información, vea [Cómo: Compilar los mismos archivos de código fuente con diferentes opciones](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Nota:**  Establezca propiedades globales en el símbolo del sistema mediante el modificador **-property** (o **-p**). También puede establecer o modificar propiedades globales para proyectos secundarios en una compilación de varios proyectos mediante el atributo `Properties` de la tarea de MSBuild. Para más información, consulte [Tarea de MSBuild](../msbuild/msbuild-task.md). |
| `xmlns` | Atributo opcional.<br /><br /> Cuando se especifica, el atributo `xmlns` debe tener el valor de `http://schemas.microsoft.com/developer/msbuild/2003`. |

### <a name="child-elements"></a>Elementos secundarios

| Elemento | Descripción |
| - | - |
| [Choose](../msbuild/choose-element-msbuild.md) | Elemento opcional.<br /><br /> Evalúa los elementos secundarios para seleccionar un conjunto de elementos `ItemGroup` o `PropertyGroup` para evaluar. |
| [Import](../msbuild/import-element-msbuild.md) | Elemento opcional.<br /><br /> Permite a un archivo del proyecto importar otro archivo del proyecto. Puede haber cero o más elementos `Import` en un proyecto. |
| [ImportGroup](../msbuild/importgroup-element.md) | Elemento opcional.<br /><br /> Contiene una colección de elementos `Import` agrupados en una condición opcional. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Elemento opcional.<br /><br /> Un elemento de agrupamiento para elementos individuales. Los elementos se especifican mediante el elemento [Item](../msbuild/item-element-msbuild.md). Puede haber cero o más elementos `ItemGroup` en un proyecto. |
| [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) | Elemento opcional.<br /><br /> Permite definir un conjunto de definiciones de elementos, que son valores de metadatos que se aplican de forma predeterminada a todos los elementos del proyecto. Con ItemDefinitionGroup, ya no es necesario usar la tarea `CreateItem` ni la tarea `CreateProperty`. |
| [ProjectExtensions](../msbuild/projectextensions-element-msbuild.md) | Elemento opcional.<br /><br /> Proporciona una manera de conservar información no relativa a MSBuild en un archivo de proyecto de MSBuild. Puede haber cero o un elementos `ProjectExtensions` en un proyecto. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Elemento opcional.<br /><br /> Un elemento de agrupamiento para propiedades individuales. Las propiedades se especifican mediante el elemento [Property](../msbuild/property-element-msbuild.md). Puede haber cero o más elementos `PropertyGroup` en un proyecto. |
| [Sdk](../msbuild/sdk-element-msbuild.md) | Elemento opcional.<br /><br /> Hace referencia a un SDK de un proyecto de MSBuild.  Este elemento se puede usar como alternativa para el atributo Sdk. |
| [Target](../msbuild/target-element-msbuild.md) | Elemento opcional.<br /><br /> Contiene un conjunto de tareas para que MSBuild las ejecute de manera secuencial. Las tareas se especifican mediante el elemento [Task](../msbuild/task-element-msbuild.md). Puede haber cero o más elementos `Target` en un proyecto. |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Elemento opcional.<br /><br /> Proporciona una manera de registrar las tareas en MSBuild. Puede haber cero o más elementos `UsingTask` en un proyecto. |

### <a name="parent-elements"></a>Elementos primarios

 Ninguno.

## <a name="see-also"></a>Vea también

- [Cómo: Especificar qué destino usar primero al compilar](../msbuild/how-to-specify-which-target-to-build-first.md)
- [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)
- [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
