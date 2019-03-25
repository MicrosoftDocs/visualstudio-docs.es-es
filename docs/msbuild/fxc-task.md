---
title: Tarea FXC | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.fxc
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), FXC task
- FXC task (MSBuild (Visual C++))
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: a0854835c1562c0797394395f07708cd0eab710d
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070511"
---
# <a name="fxc-task"></a>Tarea FXC

Use los compiladores de sombreador de HLS en el proceso de compilación.

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la tarea **FXC**.

|Parámetro|Descripción|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Parámetro **string[]** opcional.<br/><br/>Especifica uno o más directorios que se agregarán a la ruta de acceso de inclusión; si hay más de uno, sepárelos mediante punto y coma.<br/><br/>Use `/I[path]`.|
|**AdditionalOptions**|Parámetro **string** opcional.|
|**AllResourcesBound**|Parámetro **bool** opcional.<br/><br/>El compilador supondrá que todos los recursos a los que puede hacer referencia un sombreador están enlazados y en buen estado por toda la duración de la ejecución del sombreador. Disponible para Shader Model 5.1 y versiones superiores.<br/><br/>Use `/all_resources_bound`.|
|**AssemblerOutput**|Parámetro **string** opcional.<br/><br/>Especifica el contenido del archivo de salida del lenguaje de ensamblado.<br/><br/>Use `/Fc, /Fx`.<br/><br/>**NoListing**<br/>**AssemblyCode**, use `Fc`.<br/>**AssemblyCodeAndHex**, use `Fx`.|
|**AssemblerOutputFile**|Parámetro **string** opcional.<br/><br/>Especifica el nombre del archivo de listas de código de ensamblado.|
|**CompileD2DCustomEffect**|Parámetro **bool** opcional.<br/><br/>Compile un efecto personalizado de Direct2D que contenga sombreadores de píxeles. No lo use para un efecto personalizado de proceso o vértice.|
|**ConsumeExportFile**|Parámetro **string** opcional.|
|**DisableOptimizations**|Parámetro **bool** opcional.<br/><br/>Deshabilite las optimizaciones.<br/><br/>`/Od` implica `/Gfp`, a pesar de que la salida puede no ser idéntica a `/Od /Gfp`.|
|**EnableDebuggingInformation**|Parámetro **bool** opcional.<br/><br/>Habilite la información de depuración.|
|**EnableUnboundedDescriptorTables**|Parámetro **bool** opcional.<br/><br/>Informe al compilador que un sombreador puede contener una declaración de una matriz de recursos con un intervalo sin enlazar. Disponible para Shader Model 5.1 y versiones superiores.<br/><br/>Use `/enable_unbounded_descriptor_tables`.|
|**EntryPointName**|Parámetro **string** opcional.<br/><br/>Especifica el nombre del punto de entrada para el sombreador.<br/><br/>Use `/E[name]`.|
|**GenerateExportFile**|Parámetro **string** opcional.|
|**GenerateExportShaderProfile**|Parámetro **string** opcional.|
|**HeaderFileOutput**|Parámetro **string** opcional.<br/><br/>Especifica un nombre para el archivo de encabezado que contiene código de objeto.<br/><br/>Use `/Fh [name]`.|
|**ObjectFileOutput**|Parámetro **string** opcional.<br/><br/>Especifica un nombre para el archivo objeto.<br/><br/>Use `/Fo [name]`.|
|**PreprocessorDefinitions**|Parámetro **string[]** opcional.<br/><br/>Define los símbolos de preprocesamiento para el archivo de código fuente.|
|**SetRootSignature**|Parámetro **string** opcional.<br/><br/>Adjunte la firma raíz al código de bytes del sombreador. Disponible para Shader Model 5.0 y versiones superiores.<br/><br/>Use `/setrootsignature`.|
|**ShaderModel**|Parámetro **string** opcional.<br/><br/>Especifica el modelo de sombreador. Algunos tipos de sombreador solo se puede usar con modelos de sombreador recientes.<br/><br/>Use `/T [type]_[model]`.|
|**ShaderType**|Parámetro **string** opcional.<br/><br/>Especifica el tipo de sombreador.<br/><br/>Use `/T [type]_[model]`.<br/><br/>**Effect**, use `fx`.<br/>**Vertex**, use `vs`.<br/>**Pixel**, use `ps`.<br/>**Geometry**, use `gs`.<br/>**Hull**, use `hs`.<br/>**Domain**, use `ds`.<br/>**Compute**, use `cs`.<br/>**Library**, use `lib`.<br/>**RootSignature**, genere el objeto de firma raíz.|
|**Origen**|Parámetro **ITaskItem** obligatorio.|
|**SuppressStartupBanner**|Parámetro **bool** opcional.<br/><br/>Suprime la presentación de la pancarta de inicio y los mensajes de información.<br/><br/>Use `/nologo`.|
|**TrackerLogDirectory**|Parámetro **string** opcional.|
|**TreatWarningAsError**|Parámetro **bool** opcional.<br/><br/>Trata todas las advertencias del compilador como errores.<br/><br/>Para un proyecto nuevo, puede ser mejor usar `/WX` en todas las compilaciones. Resolver todas las advertencias es una forma de asegurar el menor número posible de defectos de código difíciles de encontrar.|
|**VariableName**|Parámetro **string** opcional.<br/><br/>Especifica un nombre de variable en el archivo de encabezado.<br/><br/>Use `/Vn [name]`.|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)