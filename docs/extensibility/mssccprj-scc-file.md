---
title: MSSCCPRJ. Archivo SCC (SCC File) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702464"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. Archivo SCC
Al colocar una solución o proyecto de Visual Studio bajo control de código fuente mediante el IDE, el IDE recibe dos elementos clave de información. La información procede del complemento de control de código fuente en forma de cadenas. Estas cadenas, "AuxPath" y "ProjName", son opacas para el IDE, pero el complemento las usa para buscar la solución o el proyecto en el control de versiones. Normalmente, el IDE obtiene estas cadenas la primera vez llamando a [SccGetProjPath](../extensibility/sccgetprojpath-function.md)y, a continuación, las guarda en el archivo de solución o proyecto para futuras llamadas a [SccOpenProject](../extensibility/sccopenproject-function.md). Cuando se incrustan en los archivos de solución y proyecto, las cadenas "AuxPath" y "ProjName" no se actualizan automáticamente cuando un usuario bifurca, bifurca o copia archivos de solución y proyecto que están en control de versiones. Para asegurarse de que la solución y los archivos de proyecto apuntan a su ubicación correcta en el control de versiones, los usuarios deben actualizar manualmente las cadenas. Dado que las cadenas están diseñadas para ser opacas, es posible que no siempre esté claro cómo se deben actualizar.

 El complemento de control de código fuente puede evitar este problema almacenando las cadenas "AuxPath" y "ProjName" en un archivo especial denominado archivo *MSSCCPRJ.SCC.* Es un archivo local del lado cliente que es propiedad y es mantenido por el plug-in. Este archivo nunca se coloca bajo control de código fuente, pero lo genera el complemento para cada directorio que contiene archivos controlados por código fuente. Para determinar qué archivos son archivos de solución y proyecto de Visual Studio, un complemento de control de código fuente puede comparar las extensiones de archivo con una lista estándar o proporcionada por el usuario. Una vez que el IDE detecta que un complemento es compatible con el archivo *MSSCCPRJ.SCC,* deja de incrustar las cadenas "AuxPath" y "ProjName" en los archivos de solución y proyecto, y lee esas cadenas del archivo *MSSCCPRJ.SCC* en su lugar.

 Un complemento de control de código fuente que admita el archivo *MSSCCPRJ.SCC* debe cumplir las siguientes directrices:

- Solo puede haber un archivo *MSSCCPRJ.SCC* por directorio.

- Un archivo *MSSCCPRJ.SCC* puede contener "AuxPath" y "ProjName" para varios archivos que están bajo control de código fuente dentro de un directorio determinado.

- La cadena "AuxPath" no debe tener comillas dentro de ella. Se permite tener comillas a su alrededor como delimitadores (por ejemplo, se puede utilizar un par de comillas dobles para indicar una cadena vacía). El IDE quitará todas las comillas de la cadena "AuxPath" cuando se lea desde el archivo *MSSCCPRJ.SCC.*

- La cadena "ProjName" en *MSSCCPRJ. El archivo SCC* debe coincidir `SccGetProjPath` exactamente con la cadena devuelta por la función. Si la cadena devuelta por la función tiene comillas alrededor de ella, la cadena en el archivo *MSSCCPRJ.SCC* debe tener comillas alrededor de ella, y viceversa.

- Un archivo *MSSCCPRJ.SCC* se crea o actualiza cada vez que se coloca un archivo bajo control de código fuente.

- Si se elimina un archivo *MSSCCPRJ.SCC,* un proveedor debe regenerarlo la próxima vez que realice una operación de control de código fuente relacionada con ese directorio.

- Un archivo *MSSCCPRJ.SCC* debe seguir estrictamente el formato definido.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Una ilustración del MSSCCPRJ. Formato de archivo SCC
 A continuación se muestra una muestra del formato de archivo *MSSCCPRJ.SCC* (los números de línea solo se proporcionan como guía y no deben incluirse en el cuerpo del archivo):

- [Línea 1]`SCC = This is a Source Code Control file`

- [Línea 2]

- [Línea 3]`[TestApp.sln]`

- [Línea 4]`SCC_Aux_Path = "\\server\vss\"`

- [Línea 5]`SCC_Project_Name = "$/TestApp"`

- [Línea 6]

- [Línea 7]`[TestApp.csproj]`

- [Línea 8]`SCC_Aux_Path = "\\server\vss\"`

- [Línea 9]`SCC_Project_Name = "$/TestApp"`

 La primera línea indica el propósito del archivo y sirve como firma para todos los archivos de este tipo. Esta línea debe aparecer exactamente así en todos los archivos *MSSCCPRJ.SCC:*

 `SCC = This is a Source Code Control file`

 En la siguiente sección se detalla la configuración de cada archivo, marcada por el nombre de archivo entre corchetes. Esta sección se repite para cada archivo que se realiza el seguimiento. Esta línea es un ejemplo de un `[TestApp.csproj]`nombre de archivo, a saber, . El IDE espera las dos líneas siguientes. Sin embargo, no define el estilo de los valores definidos. Las variables `SCC_Aux_Path` `SCC_Project_Name`son y .

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 No hay delimitador final en esta sección. El nombre del archivo, así como todos los literales que aparecen en el archivo, se definen en el archivo de encabezado scc.h. Para obtener más información, consulte [Cadenas utilizadas como claves para buscar un complemento](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)de control de código fuente .

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [Cadenas utilizadas como claves para encontrar un complemento de control de código fuente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
