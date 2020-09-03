---
title: MSSCCPRJ. Archivo SCC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89511b7c8b69c5793eceef7d58153dde253a4f47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702464"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. Archivo SCC
Cuando se coloca una solución de Visual Studio o un proyecto bajo control de código fuente mediante el IDE, el IDE recibe dos fragmentos de información clave. La información procede del complemento de control de código fuente en forma de cadenas. Estas cadenas, "AuxPath" y "Nombre_proyecto", son opacas para el IDE, pero las usa el complemento para buscar la solución o el proyecto en el control de versiones. Normalmente, el IDE obtiene estas cadenas la primera vez llamando a [SccGetProjPath](../extensibility/sccgetprojpath-function.md)y, a continuación, las guarda en el archivo de solución o proyecto para futuras llamadas a [SccOpenProject](../extensibility/sccopenproject-function.md). Cuando se insertan en los archivos de proyecto y de solución, las cadenas "AuxPath" y "Nombre_proyecto" no se actualizan automáticamente cuando un usuario bifurca, bifurca o copia archivos de proyecto y de solución que están en el control de versiones. Para asegurarse de que la solución y los archivos del proyecto señalan a su ubicación correcta en el control de versiones, los usuarios deben actualizar manualmente las cadenas. Dado que las cadenas están pensadas para ser opacas, puede que no siempre quede claro cómo deben actualizarse.

 El complemento de control de código fuente puede evitar este problema almacenando las cadenas "AuxPath" y "Nombre_proyecto" en un archivo especial denominado archivo *MSSCCPRJ. SCC* . Es un archivo local de cliente que es propiedad del complemento y lo mantiene. Este archivo nunca se coloca bajo control de código fuente, pero lo genera el complemento para todos los directorios que contienen archivos controlados por código fuente. Para determinar qué archivos son los archivos de proyecto y de solución de Visual Studio, un complemento de control de código fuente puede comparar las extensiones de archivo con una lista estándar o proporcionada por el usuario. Una vez que el IDE detecta que un complemento admite el archivo *MSSCCPRJ. SCC* , deja de incrustar las cadenas "AuxPath" y "Nombre_proyecto" en los archivos de proyecto y de solución, y en su lugar Lee esas cadenas del archivo *MSSCCPRJ. SCC* .

 Un complemento de control de código fuente que admita el archivo *MSSCCPRJ. SCC* debe cumplir las siguientes directrices:

- Solo puede haber un archivo *MSSCCPRJ. SCC* por directorio.

- Un archivo *MSSCCPRJ. SCC* puede contener "AuxPath" y "Nombre_proyecto" para varios archivos que están bajo control de código fuente dentro de un directorio determinado.

- La cadena "AuxPath" no debe tener comillas dentro de ella. Se permite incluir comillas alrededor como delimitadores (por ejemplo, se puede usar un par de comillas dobles para indicar una cadena vacía). El IDE quitará todas las comillas de la cadena "AuxPath" cuando se lea desde el archivo *MSSCCPRJ. SCC* .

- Cadena "Nombre_proyecto" en *MSSCCPRJ. El archivo SCC* debe coincidir exactamente con la cadena devuelta por la `SccGetProjPath` función. Si la cadena devuelta por la función contiene comillas, la cadena del archivo *MSSCCPRJ. SCC* debe tener comillas alrededor y viceversa.

- Un archivo *MSSCCPRJ. SCC* se crea o se actualiza cada vez que se coloca un archivo bajo control de código fuente.

- Si se elimina un archivo *MSSCCPRJ. SCC* , un proveedor debe volver a generarlo la próxima vez que realice una operación de control de código fuente relativa a ese directorio.

- Un archivo *MSSCCPRJ. SCC* debe seguir estrictamente el formato definido.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Ilustración de MSSCCPRJ. Formato de archivo SCC
 A continuación se muestra un ejemplo del formato de archivo *MSSCCPRJ. SCC* (los números de línea solo se proporcionan como guía y no deben incluirse en el cuerpo del archivo):

- [Línea 1] `SCC = This is a Source Code Control file`

- [Línea 2]

- [Línea 3] `[TestApp.sln]`

- [Línea 4] `SCC_Aux_Path = "\\server\vss\"`

- [Línea 5] `SCC_Project_Name = "$/TestApp"`

- [Línea 6]

- [Línea 7] `[TestApp.csproj]`

- [Línea 8] `SCC_Aux_Path = "\\server\vss\"`

- [Línea 9] `SCC_Project_Name = "$/TestApp"`

 La primera línea indica el propósito del archivo y sirve como firma para todos los archivos de este tipo. Esta línea debe aparecer exactamente igual que en todos los archivos *MSSCCPRJ. SCC* :

 `SCC = This is a Source Code Control file`

 En la siguiente sección se detallan los valores de cada archivo, marcados con el nombre de archivo entre corchetes. Esta sección se repite para cada archivo del que se realiza un seguimiento. Esta línea es una muestra de un nombre de archivo, es decir, `[TestApp.csproj]` . El IDE espera las dos líneas siguientes. No obstante, no define el estilo de los valores definidos. Las variables son `SCC_Aux_Path` y `SCC_Project_Name` .

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 No hay ningún delimitador final en esta sección. El nombre del archivo, así como todos los literales que aparecen en el archivo, se definen en el archivo de encabezado SCC. h. Para obtener más información, vea [cadenas usadas como claves para buscar un complemento de control de código fuente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [Cadenas usadas como claves para buscar un complemento de control de código fuente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
