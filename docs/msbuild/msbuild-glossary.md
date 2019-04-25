---
title: Glosario de MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f074bf7b5c7077b1c4808d7d3035be0c6366d526
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642721"
---
# <a name="msbuild-glossary"></a>Glosario de MSBuild
Estos términos se utilizan para describir Microsoft Build Engine (MSBuild) y sus componentes.

## <a name="glossary"></a>Glosario
 AssemblyFoldersEx: es una ubicación del Registro donde otros proveedores almacenan las rutas de acceso para cada versión de .NET Framework que admiten y donde la resolución en tiempo de diseño puede buscar para encontrar los ensamblados de referencia.

 Procesamiento por lotes: el procesamiento por lotes significa la división de elementos en categorías diferentes conocidas como *lotes*, basada en metadatos de elementos, seguida de la ejecución de un destino o de una tarea una vez usando cada lote. El procesamiento por lotes es el equivalente en MSBuild de la construcción de bucle for. Para obtener más información, consulte [Procesamiento por lotes](../msbuild/msbuild-batching.md).

 Ámbito de compilación: el ámbito de compilación describe un objeto de MSBuild, por ejemplo una propiedad global, que se puede ver en un proyecto y en los proyectos secundarios creados en una compilación de varios proyectos.

 Proyecto secundario: consulte *proyecto, secundario*.

 Condición: muchos elementos de MSBuild se pueden definir de forma condicional; es decir, el atributo `Condition` aparece en el elemento. El contenido de los elementos condicionales se omite, a menos que la condición se evalúe como `true`. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).

 Definición de elemento: vea *definición de elemento*.

 Emitir elemento: durante la fase de ejecución de una compilación, se pueden crear o modificar elementos. Esta operación la realizan tareas que tienen elementos `Output` secundarios que, a su vez, tienen el atributo `ItemName`. Se dice que la tarea "emite" los nuevos elementos.

 Emitir propiedad: durante la fase de ejecución de una compilación, se pueden crear o modificar propiedades. Esta operación la realizan tareas que tienen elementos `Output` secundarios que, a su vez, tienen el atributo `PropertyName`. Se dice que la tarea "emite" la nueva propiedad.

 Fase de evaluación: la evaluación es la primera fase de la compilación de un proyecto. Todas las propiedades y elementos se evalúan en el orden en que aparecen en el proyecto. Los proyectos importados se evalúan según se encuentran en el proyecto. Los destinos y las tareas no se ejecutan hasta la fase de ejecución, y las propiedades o elementos que puedan declarar o emitir se omiten durante la evaluación.

 Fase de ejecución: la ejecución es la segunda fase de la compilación de un proyecto. Se compilan los destinos seleccionados y se ejecutan las tareas. Se pueden crear o modificar propiedades y elementos mediante la comparación con sus valores de evaluación.

 Función, propiedad: consulte *función de propiedad*.

 Función, elemento: consulte función de elemento.

 Elemento: los elementos son entradas en el sistema de compilación y se agrupan en tipos de elementos basados en los nombres de elementos. Los elementos representan normalmente archivos. Dado que el nombre de los elementos viene determinado por el tipo de elemento al que pertenecen, los términos *elemento* y *valor de elemento* se pueden utilizar indistintamente. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).

 Definición de elemento: los grupos de definiciones de elementos contienen definiciones que agregan metadatos predeterminados a cualquier tipo de elemento. Al igual que los metadatos conocidos, los metadatos predeterminados están asociados a todos los elementos del tipo de elemento especificado. Los metadatos predeterminados se pueden reemplazar explícitamente en una definición de elemento. Para obtener más información, vea [Definiciones de elementos](../msbuild/item-definitions.md).

 Función de elemento: las funciones de elemento obtienen información sobre los elementos del proyecto. Estas funciones simplifican la obtención de elementos Distinct() y son más rápidas que si se recorren en bucle los elementos. Hay funciones para manipular las rutas de acceso y las cadenas de los elementos. Para obtener más información, vea [Funciones de elementos](../msbuild/item-functions.md)

 Metadatos de elemento: consulte *metadatos, elemento*.

 Tipo de elemento: los tipos de elemento son listas de elementos con nombre que se pueden usar como parámetros de las tareas. Las tareas utilizan los valores de los elementos para llevar a cabo los pasos del proceso de compilación. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).

 Metadatos, elemento: los metadatos de elemento son una colección de pares de nombre y valor asociada a un elemento. Los metadatos proporcionan información descriptiva para el elemento y son opcionales, salvo los metadatos conocidos. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).

 Metadatos, conocidos: los metadatos conocidos son metadatos de elemento de solo lectura que se inicializan utilizando un valor predefinido. Los metadatos conocidos proporcionan información descriptiva para un elemento que hace referencia a un archivo. Por ejemplo, el valor de los metadatos conocidos con denominación `FullPath` son la ruta de acceso completa del archivo al que se hace referencia. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).

 Compatibilidad con múltiples versiones (multi-targeting): es la capacidad de un proyecto de aplicación o ensamblado para tener como destino muchos CLR y marcos diferentes de MSBuild y Visual Studio.

 Perfil: es un subconjunto del marco completo. Se utiliza para minimizar la cantidad que hay que descargar en un equipo.

 Archivo del proyecto: un archivo del proyecto contiene el script de MSBuild que controla la compilación. Los archivos de proyecto tienen normalmente una extensión que finaliza con *proj*, como *.csproj* o *.vbproj*. Los archivos del proyecto pueden importar archivos de propiedad y archivos de destino.

 Propiedad: una propiedad es un par clave-valor que se utiliza para controlar el proceso de compilación. Para más información, vea [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

 Propiedad, entorno: una propiedad de entorno es una propiedad que se inicializa automáticamente en el valor de una variable de entorno del sistema que tiene el mismo nombre. Para más información, vea [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

 Archivo de propiedad: un archivo de propiedad es un archivo del proyecto que contiene principalmente grupos de propiedades y grupos de elementos que guían la compilación. Por convención, tiene la extensión de archivo *.props*. Los archivos de propiedad se importan normalmente al principio de los archivos del proyecto asociados.

 Propiedad, función: una función de propiedad es una propiedad o método del sistema que se puede usar para evaluar scripts de MSBuild. Los métodos de propiedad se pueden utilizar para leer la hora del sistema, comparar cadenas, buscar coincidencias de expresiones regulares y realizar otras acciones. Para obtener más información, vea [Funciones de propiedad](../msbuild/property-functions.md).

 Función de propiedad, anidada: las funciones de propiedad se pueden combinar para formar funciones más complejas. Por ejemplo,

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

 Para obtener más información, vea [Funciones de propiedad](../msbuild/property-functions.md).

 Propiedad, global: una propiedad global es un par clave-valor que se utiliza para controlar el proceso de compilación. Las propiedades globales se establecen en un símbolo del sistema o mediante el atributo `Properties` de una [tarea de MSBuild](../msbuild/msbuild-task.md) y no se pueden modificar durante la fase de evaluación de una compilación. Para más información, vea [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

 Propiedad, local: una propiedad local es un par clave-valor que se utiliza para controlar el proceso de compilación. Este término se utiliza solamente para distinguir una propiedad que no es una propiedad global.

 Propiedad, Registro: una propiedad del Registro tiene un valor que se establece utilizando una sintaxis especial que lee el valor de una subclave del Registro del sistema. Para más información, vea [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

 Propiedad, reservada: una propiedad reservada es un par clave-valor que se utiliza para controlar el proceso de compilación. Las propiedades reservadas se inicializan automáticamente en los valores predefinidos. Para más información, vea [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

 Ámbito del proyecto: el ámbito del proyecto describe un objeto de MSBuild, por ejemplo una propiedad local, que solo está visible en el archivo del proyecto contenedor y para los proyectos que importa.

 Proyecto, secundario: los proyectos secundarios los crea la tarea de MSBuild durante la compilación de un proyecto. Este nuevo proyecto es un elemento secundario del proyecto que contiene o importa el destino que contiene la tarea de MSBuild. El proyecto secundario hereda las propiedades globales del proyecto principal, a menos que el atributo `Properties` las modifique.

 Lista de redistribuciones: lista de ensamblados que corresponden a un marco determinado.

 Ensamblado de referencia: es un ensamblado que se usa en tiempo de diseño para crear una aplicación. Un ensamblado de referencia puede no tener el código real ni las interfaces privadas y solo tener los metadatos e interfaces públicas.

 Propiedad del Registro: consulte *propiedad, Registro*.

 Destino: un destino agrupa tareas en un orden concreto y expone secciones del archivo del proyecto como puntos de entrada en el proceso de compilación. Para obtener más información, consulte [Destinos](../msbuild/msbuild-targets.md).

 Destino, compilación: consulte destino, ejecución.

 Destino, evaluación: debido a la compilación incremental, los destinos se deben analizar ante posibles cambios en propiedades y elementos. Aunque se omita el destino, estos cambios deben realizarse. La evaluación de un destino significa la realización de este análisis y la introducción de estos cambios. Para obtener más información, vea [Compilaciones incrementales](../msbuild/incremental-builds.md).

 Destino, ejecución: la ejecución de un destino significa su evaluación y la ejecución de todas las tareas que no tienen condiciones o cuyas condiciones se evalúan como true. Durante la compilación incremental los destinos se pueden omitir o ejecutar, pero siempre se evalúan. Para obtener más información, vea destino, evaluación.

 Destino, ejecución: un destino con una condición que se evalúa como false no se ejecuta; es decir, no tiene ningún efecto en la compilación. Los destinos activos se ejecutan o se omiten. En cualquiera de los dos casos, el destino se evalúa. Para obtener más información, vea destino, evaluación.

 Destino, omisión: si la compilación incremental determina que todos los archivos de salida están actualizados, el destino se omite; es decir, el destino se evalúa pero las tareas dentro del destino no se ejecutan. Para obtener más información, vea destino, evaluación.

 Moniker del marco de destino: es un nombre que describe el marco (como .NET Framework, Silverlight, etc.), la versión y el perfil (por ejemplo, cliente, servidor, etc.) de destino.

 Paquete de destino: es la lista de ensamblados que se distribuyen con un marco determinado y el conjunto de ensamblados de referencia para ese marco.

 Archivo de destinos: un archivo de destinos es un archivo del proyecto que contiene principalmente los destinos y las tareas que guían la compilación. Por convención, tiene la extensión de archivo *.targets*. Los archivos de destinos se importan normalmente al final de los archivos del proyecto asociados.

 Tareas: las tareas son unidades de código ejecutable que se utilizan en proyectos de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] para realizar operaciones de compilación. Por ejemplo, una tarea podría compilar archivos de entrada o ejecutar una herramienta externa. Para obtener más información, consulte [Tareas](../msbuild/msbuild-tasks.md).

 Transformación: una transformación es una conversión unívoca de una colección de elementos en otra. Además de permitir que un proyecto convierta colecciones de elementos, una transformación permite que un destino identifique una asignación directa entre sus entradas y salidas. Para obtener más información, consulte [Transformaciones](../msbuild/msbuild-transforms.md).

 Metadatos conocidos: vea *metadatos, conocidos*.

## <a name="see-also"></a>Vea también
- [MSBuild](../msbuild/msbuild.md)