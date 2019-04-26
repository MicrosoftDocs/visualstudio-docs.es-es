---
title: Línea de comandos del evento anterior/posterior a la compilación (Cuadro de diálogo)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEventsBuilder
- vb.ProjectPropertiesBuildEventsBuilder
helpviewer_keywords:
- $(SolutionExt)
- $(ProjectDir)
- $(TargetPath)
- $(ProjectExt)
- $(TargetFileName)
- $(PlatformName)
- $(SolutionName)
- macros, build events
- $(SolutionPath)
- $(ProjectPath)
- $(ProjectFileName)
- $(DevEnvDir)
- $(TargetName)
- $(TargetDir)
- $(SolutionDir)
- $(TargetExt)
- $(OutDir)
- $(ConfigurationName)
- $(SolutionFileName)
- $(ProjectName)
- build events, macros
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 977bd72b478d2106f687d3666aad574a63ca68ec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969064"
---
# <a name="pre-build-eventpost-build-event-command-line-dialog-box"></a>Línea de comandos del evento anterior/posterior a la compilación (Cuadro de diálogo)
Puede escribir eventos anteriores o posteriores a la compilación para la [página Eventos de compilación, Diseñador de proyectos (C#)](../../ide/reference/build-events-page-project-designer-csharp.md) directamente en el cuadro de edición o puede seleccionar macros anteriores o posteriores a la compilación de una lista de macros disponibles.

> [!NOTE]
> Los eventos anteriores a la compilación no se ejecutan si el proyecto está actualizado y no se desencadena ninguna compilación.

## <a name="ui-element-list"></a>Lista de elementos de la interfaz de usuario
 **Cuadro de edición de línea de comandos**

 Contiene los eventos que se van a ejecutar, ya sean anteriores o posteriores a la compilación.

> [!NOTE]
> Agregue una instrucción `call` antes de todos los comandos posteriores a la compilación que ejecutan archivos .bat. Por ejemplo: `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.

 **Macros**

 Expande el cuadro de edición para mostrar una lista de macros que se van a insertar en el cuadro de edición de la línea de comandos.

 **Tabla de macros**

 Se enumeran las macros disponibles y su valor. Vea la sección Macros siguiente para obtener una descripción de cada una. Al insertar las macros en el cuadro de edición de la línea de comandos, solo puede seleccionarlas de una en una.

 **Insertar**

 Inserta en el cuadro de edición de la línea de comandos la macro seleccionada en la tabla de macros.

### <a name="macros"></a>Macros
 Puede usar cualquiera de estas macros para especificar las ubicaciones de los archivos o para obtener el nombre real del archivo de entrada en el caso de las selecciones múltiples. Estas macros no distinguen entre mayúsculas y minúsculas.

|Macro|Descripción|
|-----------|-----------------|
|`$(ConfigurationName)`|El nombre de la configuración del proyecto actual (por ejemplo, "Depuración").|
|`$(OutDir)`|Ruta de acceso al directorio de archivos de salida relativo al directorio del proyecto. Se resuelve en el valor de la propiedad Directorio de salida. Incluye la barra diagonal inversa final “\\”.|
|`$(DevEnvDir)`|El directorio de instalación de Visual Studio (definido como unidad y ruta de acceso) incluye la barra diagonal inversa final "\\".|
|`$(PlatformName)`|El nombre de la plataforma de destino actual. Por ejemplo, "CualquierCPU".|
|`$(ProjectDir)`|El directorio del proyecto (definido como unidad y ruta de acceso) incluye la barra diagonal inversa final "\\".|
|`$(ProjectPath)`|El nombre de ruta de acceso absoluta del proyecto (definido como unidad, ruta de acceso, nombre base y extensión de archivo).|
|`$(ProjectName)`|El nombre base del proyecto.|
|`$(ProjectFileName)`|El nombre de archivo del proyecto (definido como nombre base y extensión de archivo).|
|`$(ProjectExt)`|La extensión de archivo del proyecto. Incluye el "." antes de la extensión de archivo.|
|`$(SolutionDir)`|El directorio de la solución (definido como unidad y ruta de acceso) incluye la barra diagonal inversa final "\\".|
|`$(SolutionPath)`|El nombre de ruta de acceso absoluta de la solución (definido como unidad, ruta de acceso, nombre base y extensión de archivo).|
|`$(SolutionName)`|El nombre base de la solución.|
|`$(SolutionFileName)`|El nombre de archivo de la solución (definido como nombre base y extensión de archivo).|
|`$(SolutionExt)`|La extensión de archivo de la solución. Incluye el "." antes de la extensión de archivo.|
|`$(TargetDir)`|El directorio del archivo de salida principal de la compilación (definido como unidad y ruta de acceso). Incluye la barra diagonal inversa final "\\".|
|`$(TargetPath)`|El nombre de ruta de acceso absoluta del archivo de salida principal de la compilación (definido como unidad, ruta de acceso, nombre base y extensión de archivo).|
|`$(TargetName)`|El nombre base del archivo de salida principal de la compilación.|
|`$(TargetFileName)`|El nombre de archivo del archivo de salida principal de la generación (definido como nombre base y extensión de archivo).|
|`$(TargetExt)`|La extensión de archivo del archivo de salida principal de la compilación. Incluye el "." antes de la extensión de archivo.|

## <a name="see-also"></a>Vea también

- [Especificar eventos de compilación personalizados en Visual Studio](../../ide/specifying-custom-build-events-in-visual-studio.md)
- [Página Eventos de compilación, (Diseñador de proyectos) (C#)](../../ide/reference/build-events-page-project-designer-csharp.md)
- [Cómo: Especificar eventos de compilación (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Cómo: Especificar eventos de compilación (C#)](../../ide/how-to-specify-build-events-csharp.md)