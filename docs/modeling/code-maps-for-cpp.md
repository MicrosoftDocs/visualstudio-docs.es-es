---
title: Ver las dependencias entre los archivos de origen y encabezado de C++
description: Proporciona información sobre los mapas de código para proyectos de C++.
ms.date: 05/16/2018
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
ms.custom: SEO-VS-2020
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 93ac1f7364e23ef9ed2b44ecd1c536a7ab2b3d40
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389675"
---
# <a name="code-maps-for-c-projects"></a>Mapas de código para proyectos de C++

Si desea crear mapas más completos para proyectos de C++, establezca en dichos proyectos la opción del compilador de información de examen (**/FR**). Si no, aparece un mensaje que le solicita establecer esta opción. Si selecciona **Aceptar**, la opción se establece solamente en el mapa actual. Si lo desea, puede ocultar el mensaje para todos los mapas posteriores.

Al abrir una solución que contiene proyectos de Visual C++, podría llevar algún tiempo la actualización de la base de datos de IntelliSense. Durante este tiempo, es posible que no pueda crear mapas de código para los archivos de encabezado (*.h* o ) hasta que la base de datos de `#include` IntelliSense termine de actualizarse. Puede supervisar el progreso de actualización en la barra de estado de Visual Studio.

- Para ver las dependencias entre todos los archivos de origen y los archivos de encabezado de la solución, seleccione **Architecture** Generate Graph of Include Files (Generar arquitectura  >  **de gráfico de archivos de incluir).**

   ![Gráfico de dependencias para código nativo](../modeling/media/dependencygraphgeneral_nativecode.png)

- Para ver las dependencias entre el archivo abierto actualmente y los archivos de código fuente y de encabezado relacionados, abra el archivo de origen o el archivo de encabezado. Abra el menú contextual del archivo desde cualquier parte del archivo. Elija **Generar gráficos de archivos de inclusión**.

   ![Gráfico de dependencias de primer nivel para archivo .h](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>Solución de problemas de mapas de código para código de C y C++

Estos elementos no se admiten para código de C y C++:

- Los tipos base no aparecen en los mapas que incluyen la jerarquía primaria.

- La mayoría de los elementos de menú **Mostrar** no están disponibles para el código de C y C++.

Estos problemas pueden producirse al crear mapas de código para código de C y C++:

|**Problema**|**Causa posible**|**Resolución**|
|-|-|-|
|El mapa de código no se generó.|No se compiló correctamente ningún proyecto de la solución.|Corrija los errores de compilación que se produjeron y, después, vuelva a generar el mapa.|
|Visual Studio deja de responder al intentar generar un mapa de código desde el **menú Arquitectura.**|El archivo de base de datos de programa (.pdb) podría estar dañado.<br /><br /> Un archivo .pdb almacena la información de depuración, como tipo, método e información del archivo de código fuente.|Recompile la solución y, a continuación, inténtelo de nuevo.|
|Cierta configuración de la base de datos de navegador de IntelliSense está deshabilitada.|Es posible que se deshabilite cierta configuración de IntelliSense en Visual Studio **cuadro de diálogo** Opciones de configuración.|Active los valores para habilitarla.<br /><br /> Vea [Opciones, Editor de texto, C/C++, Opciones avanzadas.](../ide/reference/options-text-editor-c-cpp-advanced.md)|
|Aparece el mensaje **Métodos desconocidos** en un nodo de método.<br /><br /> Este problema se produce porque no se puede resolver el nombre del método.|El archivo binario podría no tener una tabla de reubicación base.|Active la opción **/FIXED:NO** en el vinculador.|
||El archivo de base de datos de programa (.pdb) podría no estar compilado.<br /><br /> Un archivo .pdb almacena la información de depuración, como tipo, método e información del archivo de código fuente.|Active la opción **/DEBUG** en el vinculador.|
||No se puede abrir o encontrar el archivo .pdb en las ubicaciones esperadas.|Asegúrese de que existe el archivo .pdb en las ubicaciones esperadas.|
||Se ha quitado la información de depuración del archivo .pdb.|Si se ha usado la opción **/PDBSTRIPPED** en el vinculador, incluya el archivo .pdb completo en su lugar.|
||El llamador no es una función y, o bien es un código thunk en el archivo binario o es un puntero en la sección de datos.|Cuando el llamador es un código thunk, intente usar `_declspec(dllimport)` para evitar el código thunk.|

## <a name="see-also"></a>Vea también

- [Asignación de dependencias con mapas de código](../modeling/map-dependencies-across-your-solutions.md)
