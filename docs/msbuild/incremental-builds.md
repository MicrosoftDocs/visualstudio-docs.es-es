---
title: Compilaciones incrementales | Microsoft Docs
description: Obtenga información sobre las compilaciones incrementales de MSBuild, que están optimizadas para que no se ejecuten los archivos de salida actualizados.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, incremental builds
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1237128852cec39ff49204e1c269f10153b42ab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914084"
---
# <a name="incremental-builds"></a>Compilaciones incrementales

Las compilaciones incrementales son compilaciones que se optimizan para que no se ejecuten los destinos que tienen archivos de salida que están actualizados con respecto a sus archivos de entrada correspondientes. Un elemento de destino puede tener un atributo `Inputs`, que indica qué elementos el destino espera como entrada, y un atributo `Outputs`, que indica qué elementos genera como salida. MSBuild intenta buscar una asignación 1 a 1 entre los valores de estos atributos. Si existe una asignación 1 a 1, MSBuild compara la marca de tiempo de cada elemento de entrada con la marca de tiempo de su elemento de salida correspondiente. Los archivos de salida que no tienen ninguna asignación 1 a 1 se comparan con todos los archivos de entrada. Un elemento se considera actualizado si su archivo de salida tiene una antigüedad igual o inferior a la de su archivo o archivos de entrada.

> [!NOTE]
> Cuando MSBuild evalúa los archivos de entrada, solo se tiene en cuenta el contenido de la lista en la ejecución actual. Los cambios que se realicen en la lista desde la última compilación no harán que un destino se desproteja automáticamente.

Si todos los elementos de salida están actualizados, MSBuild omite el destino. Esta *compilación incremental* del destino puede mejorar significativamente la velocidad de compilación. Si solo están actualizados algunos archivos, MSBuild ejecuta el destino pero omite los elementos actualizados, actualizando de ese modo todos los elementos. Este proceso se conoce como *compilación incremental parcial*.

Las asignaciones 1 a 1 son generadas normalmente por transformaciones de elementos. Para obtener más información, consulte [Transformaciones](../msbuild/msbuild-transforms.md).

 Considere el destino siguiente.

```xml
<Target Name="Backup" Inputs="@(Compile)"
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">
    <Copy SourceFiles="@(Compile)" DestinationFiles=
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />
</Target>
```

El conjunto de archivos representado por el tipo de elemento `Compile` se copia en un directorio de copia de seguridad. Los archivos de copia de seguridad tienen la extensión de nombre de archivo *.bak*. Si los archivos representados por el tipo de elemento `Compile`, o los archivos de copia de seguridad correspondientes, no se eliminan o modifican después de ejecutarse el destino Backup, este destino se omite en compilaciones subsiguientes.

## <a name="output-inference"></a>Inferencia de salida

MSBuild compara los atributos `Inputs` y `Outputs` de un destino para determinar si el destino tiene que ejecutarse. Idealmente, el conjunto de archivos que existe después de completarse una compilación incremental debe permanecer inalterado se ejecuten o no los destinos asociados. Dado que las propiedades y los elementos creados o modificados por tareas pueden afectar a la compilación, MSBuild debe deducir sus valores aunque el destino que los afecta se omita. Este proceso se conoce como *inferencia de salida*.

Existen tres casos:

- El destino tiene un atributo `Condition` que se evalúa como `false`. En este caso, el destino no se ejecuta y no tiene ningún efecto en la compilación.

- El destino tiene salidas sin actualizar y se ejecuta para actualizarlas.

- El destino no tiene salidas sin actualizar y se omite. MSBuild evalúa el destino y realiza cambios en los elementos y las propiedades como si el destino se hubiera ejecutado.

Para admitir la compilación incremental, las tareas deben asegurarse de que el valor de atributo `TaskParameter` de cualquier elemento `Output` sea igual a un parámetro de entrada de tarea. Estos son algunos ejemplos:

```xml
<CreateProperty Value="123">
    <Output PropertyName="Easy" TaskParameter="Value" />
</CreateProperty>
```

Este código crea la propiedad Easy, que tiene el valor "123" tanto si el destino se ejecuta o se omite como si no.

A partir de MSBuild 3.5, la inferencia de salida se realiza automáticamente en los grupos de elementos y propiedades de un destino. Las tareas `CreateItem` no se requieren en un destino y se deben evitar. Además, las tareas `CreateProperty` deben utilizarse en un destino solamente para determinar si se ha ejecutado un destino.

Antes de MSBuild 3.5, puede usar la tarea [CreateItem](../msbuild/createitem-task.md).

## <a name="determine-whether-a-target-has-been-run"></a>Determinar si se ha ejecutado un destino

Debido a la inferencia de salida, se tiene que agregar una tarea `CreateProperty` a un destino para examinar las propiedades y los elementos con el fin de poder determinar si se ha ejecutado el destino. Agregue la tarea `CreateProperty` al destino y proporciónele un elemento `Output` cuyo valor de atributo `TaskParameter` sea "ValueSetByTask".

```xml
<CreateProperty Value="true">
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />
</CreateProperty>
```

Este código crea la propiedad CompileRan y le proporciona el valor `true`, pero solo si se ejecuta el destino. Si el destino se omite, no se crea CompileRan.

## <a name="see-also"></a>Vea también

- [Destinos](../msbuild/msbuild-targets.md)
