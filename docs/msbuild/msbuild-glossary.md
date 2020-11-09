---
title: Glosario de MSBuild
description: Obtenga información sobre los términos del glosario de Microsoft Build Engine (MSBuild) que describen el motor de compilación y sus componentes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f42d7945656a3f0e3cfbe11f80db26b7e5c124d3
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046324"
---
# <a name="msbuild-glossary"></a>Glosario de MSBuild

Estos términos se utilizan para describir Microsoft Build Engine (MSBuild) y sus componentes.

## <a name="glossary"></a>Glosario

AssemblyFoldersEx\
Es una ubicación del Registro donde otros proveedores almacenan las rutas de acceso para cada versión de .NET Framework que admiten y donde la resolución en tiempo de diseño puede buscar para encontrar los ensamblados de referencia.

batching\
El procesamiento por lotes significa la división de elementos en categorías diferentes conocidas como *lotes* , basada en metadatos de elementos, seguida de la ejecución de un destino o de una tarea una vez utilizando cada lote. El procesamiento por lotes es el equivalente en MSBuild de la construcción de bucle for. Para obtener más información, consulte [Procesamiento por lotes](../msbuild/msbuild-batching.md).

build-scope\
El ámbito de compilación describe un objeto de MSBuild, por ejemplo una propiedad global, que se puede ver en un proyecto y en los proyectos secundarios creados en una compilación de varios proyectos.

child project\
Consulte *proyecto, secundario*.

condition\
Muchos elementos de MSBuild se pueden definir de forma condicional; es decir, el atributo `Condition` aparece en el elemento. El contenido de los elementos condicionales se omite, a menos que la condición se evalúe como `true`. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).

definition, item\
Consulte *definición de elemento*.

emit item\
Durante la fase de ejecución de una compilación, se pueden crear o modificar elementos. Esta operación la realizan tareas que tienen elementos `Output` secundarios que, a su vez, tienen el atributo `ItemName`. Se dice que la tarea "emite" los nuevos elementos.

emit property\
Durante la fase de ejecución de una compilación, se pueden crear o modificar propiedades. Esta operación la realizan tareas que tienen elementos `Output` secundarios que, a su vez, tienen el atributo `PropertyName`. Se dice que la tarea "emite" la nueva propiedad.

evaluation phase\
La evaluación es la primera fase de la compilación de un proyecto. Todas las propiedades y elementos se evalúan en el orden en que aparecen en el proyecto. Los proyectos importados se evalúan según se encuentran en el proyecto. Los destinos y las tareas no se ejecutan hasta la fase de ejecución, y las propiedades o elementos que puedan declarar o emitir se omiten durante la evaluación.

execution phase\
La ejecución es la segunda fase de la compilación de un proyecto. Se compilan los destinos seleccionados y se ejecutan las tareas. Se pueden crear o modificar propiedades y elementos mediante la comparación con sus valores de evaluación.

function, property\
Consulte *función de propiedad*.

function, item\
Vea función de elemento.

item\
Los elementos son entradas en el sistema de compilación y se agrupan en tipos de elementos basados en los nombres de elementos. Los elementos representan normalmente archivos. Dado que el nombre de los elementos viene determinado por el tipo de elemento al que pertenecen, los términos *elemento* y *valor de elemento* se pueden utilizar indistintamente. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).

item definition\
Los grupos de definiciones de elementos contienen definiciones de elementos que agregan metadatos predeterminados a cualquier tipo de elemento. Al igual que los metadatos conocidos, los metadatos predeterminados están asociados a todos los elementos del tipo de elemento especificado. Los metadatos predeterminados se pueden reemplazar explícitamente en una definición de elemento. Para obtener más información, vea [Definiciones de elementos](../msbuild/item-definitions.md).

item function\
Las funciones de elemento obtienen información sobre los elementos del proyecto. Estas funciones simplifican la obtención de elementos Distinct() y son más rápidas que si se recorren en bucle los elementos. Hay funciones para manipular las rutas de acceso y las cadenas de los elementos. Para más información, consulte [Funciones de elementos](../msbuild/item-functions.md).

item metadata\
Consulte *metadatos, elemento*.

item type\
Los tipos de elemento son listas de elementos con nombre que se pueden usar como parámetros de las tareas. Las tareas utilizan los valores de los elementos para llevar a cabo los pasos del proceso de compilación. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).

metadata, item\
Los metadatos de elemento son una colección de pares de nombre y valor asociada a un elemento. Los metadatos proporcionan información descriptiva para el elemento y son opcionales, salvo los metadatos conocidos. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).

metadata, well-known\
Los metadatos conocidos son metadatos de elemento de solo lectura que se inicializan utilizando un valor predefinido. Los metadatos conocidos proporcionan información descriptiva para un elemento que hace referencia a un archivo. Por ejemplo, el valor de los metadatos conocidos con denominación `FullPath` son la ruta de acceso completa del archivo al que se hace referencia. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).

multitargeting\
Es la capacidad de un proyecto de aplicación o ensamblado para tener como destino muchos CLR y marcos diferentes de MSBuild y Visual Studio.

profile\
Es un subconjunto del marco completo. Se utiliza para minimizar la cantidad que hay que descargar en un equipo.

project file\
Un archivo del proyecto contiene el script de MSBuild que controla la compilación. Los archivos de proyecto tienen normalmente una extensión que finaliza con *proj* , como *.csproj* o *.vbproj*. Los archivos del proyecto pueden importar archivos de propiedad y archivos de destino.

property\
Una propiedad es un par clave-valor que se utiliza para controlar el proceso de compilación. Para más información, vea [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

property, environment\
Una propiedad de entorno es una propiedad que se inicializa automáticamente en el valor de una variable de entorno del sistema que tiene el mismo nombre. Para más información, vea [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

property file\
Un archivo de propiedad es un archivo del proyecto que contiene principalmente grupos de propiedades y grupos de elementos que guían la compilación. Por convención, tiene la extensión de archivo *.props*. Los archivos de propiedad se importan normalmente al principio de los archivos del proyecto asociados.

property, function\
Una función de propiedad es una propiedad o método del sistema que se puede utilizar para evaluar scripts de MSBuild. Los métodos de propiedad se pueden utilizar para leer la hora del sistema, comparar cadenas, buscar coincidencias de expresiones regulares y realizar otras acciones. Para obtener más información, vea [Funciones de propiedad](../msbuild/property-functions.md).

property function, nested\
Las funciones de propiedad se pueden combinar para formar funciones más complejas. Por ejemplo,

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

Para obtener más información, vea [Funciones de propiedad](../msbuild/property-functions.md).

property, global\
Una propiedad global es un par clave-valor que se utiliza para controlar el proceso de compilación. Las propiedades globales se establecen en un símbolo del sistema o mediante el atributo `Properties` de una [tarea de MSBuild](../msbuild/msbuild-task.md) y no se pueden modificar durante la fase de evaluación de una compilación. Para más información, vea [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

property, local\
Una propiedad local es un par clave-valor que se utiliza para controlar el proceso de compilación. Este término se utiliza solamente para distinguir una propiedad que no es una propiedad global.

property, registry\
Una propiedad del Registro tiene un valor que se establece utilizando una sintaxis especial que lee el valor de una subclave del Registro del sistema. Para más información, vea [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

property, reserved\
Una propiedad reservada es un par clave-valor que se utiliza para controlar el proceso de compilación. Las propiedades reservadas se inicializan automáticamente en los valores predefinidos. Para más información, vea [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

project-scope\
El ámbito del proyecto describe un objeto de MSBuild, por ejemplo una propiedad local, que solo está visible en el archivo del proyecto contenedor y para los proyectos que importa.

project, child\
Los proyectos secundarios los crea la tarea de MSBuild durante la compilación de un proyecto. Este nuevo proyecto es un elemento secundario del proyecto que contiene o importa el destino que contiene la tarea de MSBuild. El proyecto secundario hereda las propiedades globales del proyecto principal, a menos que el atributo `Properties` las modifique.

redist list\
lista de redistribuciones: lista de ensamblados que corresponden a un marco determinado.

reference assembly\
Es un ensamblado que se utiliza en tiempo de diseño para crear una aplicación. Un ensamblado de referencia puede no tener el código real ni las interfaces privadas y solo tener los metadatos e interfaces públicas.

registry property\
Consulte *propiedad, registro*.

target\
Un destino agrupa tareas en un orden concreto y expone secciones del archivo del proyecto como puntos de entrada en el proceso de compilación. Para obtener más información, consulte [Destinos](../msbuild/msbuild-targets.md).

target, building\
Vea destino, ejecución.

target, evaluating\
Debido a la compilación incremental, los destinos se deben analizar ante posibles cambios en propiedades y elementos. Aunque se omita el destino, estos cambios deben realizarse. La evaluación de un destino significa la realización de este análisis y la introducción de estos cambios. Para obtener más información, vea [Compilaciones incrementales](../msbuild/incremental-builds.md).

target, executing\
La ejecución de un destino significa su evaluación y la ejecución de todas las tareas que no tienen condiciones o cuyas condiciones se evalúan como true. Durante la compilación incremental los destinos se pueden omitir o ejecutar, pero siempre se evalúan. Para obtener más información, vea destino, evaluación.

target, running\
Un destino con una condición que se evalúa como false no se ejecuta; es decir, no tiene ningún efecto en la compilación. Los destinos activos se ejecutan o se omiten. En cualquiera de los dos casos, el destino se evalúa. Para obtener más información, vea destino, evaluación.

target, skipping\
Si la compilación incremental determina que todos los archivos de salida están actualizados, el destino se omite; es decir, el destino se evalúa pero las tareas dentro del destino no se ejecutan. Para obtener más información, vea destino, evaluación.

target framework moniker\
Es un nombre que describe el marco (como .NET Framework, Silverlight, etc.), la versión y el perfil (por ejemplo, cliente, servidor, etc.) de destino.

targeting pack\
Es la lista de ensamblados que se distribuyen con un marco determinado y el conjunto de ensamblados de referencia para ese marco.

targets file\
Un archivo de destinos es un archivo del proyecto que contiene principalmente los destinos y las tareas que guían la compilación. Por convención, tiene la extensión de archivo *.targets*. Los archivos de destinos se importan normalmente al final de los archivos del proyecto asociados.

task\
Las tareas son unidades de código ejecutable que se utilizan en proyectos de MSBuild para realizar operaciones de compilación. Por ejemplo, una tarea podría compilar archivos de entrada o ejecutar una herramienta externa. Para obtener más información, consulte [Tareas](../msbuild/msbuild-tasks.md).

transform\
Una transformación es una conversión unívoca de una colección de elementos en otra. Además de permitir que un proyecto convierta colecciones de elementos, una transformación permite que un destino identifique una asignación directa entre sus entradas y salidas. Para obtener más información, consulte [Transformaciones](../msbuild/msbuild-transforms.md).

well-known metadata\
Consulte *metadatos, conocidos*.

## <a name="see-also"></a>Vea también

- [MSBuild](../msbuild/msbuild.md)
