---
title: MSSCCPRJ. SCC File | Microsoft Docs
description: Obtenga información sobre MSSCCPRJ. Archivo SCC, que es un archivo local del lado cliente que usa el complemento control de código fuente, que funciona con el SDK Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e006e4462522f4c464f40e0656dcef4d32c85fb7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899256"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. Archivo SCC
Al colocar una solución Visual Studio proyecto bajo control de código fuente mediante el IDE, el IDE recibe dos fragmentos clave de información. La información procede del complemento de control de código fuente en forma de cadenas. Estas cadenas, "AuxPath" y "ProjName", son opacas para el IDE, pero el complemento las usa para buscar la solución o el proyecto en el control de versiones. Normalmente, el IDE obtiene estas cadenas por primera vez mediante una llamada a [SccGetProjPath](../extensibility/sccgetprojpath-function.md)y, a continuación, las guarda en la solución o el archivo de proyecto para futuras llamadas a [SccOpenProject](../extensibility/sccopenproject-function.md). Cuando se insertan en los archivos de solución y proyecto, las cadenas "AuxPath" y "ProjName" no se actualizan automáticamente cuando un usuario bifurca, bifurca o copia los archivos de solución y proyecto que están en control de versiones. Para asegurarse de que los archivos de solución y proyecto apuntan a su ubicación correcta en el control de versiones, los usuarios deben actualizar manualmente las cadenas. Dado que las cadenas están pensadas para ser opacas, puede que no siempre esté claro cómo se deben actualizar.

 El complemento de control de código fuente puede evitar este problema almacenando las cadenas "AuxPath" y "ProjName" en un archivo especial denominado *archivo MSSCCPRJ.SCC.* Es un archivo local del lado cliente que es propiedad del complemento y lo mantiene. Este archivo nunca se coloca bajo control de código fuente, pero lo genera el complemento para cada directorio que contiene archivos controlados por código fuente. Para determinar qué archivos se Visual Studio solución y archivos de proyecto, un complemento de control de código fuente puede comparar las extensiones de archivo con una lista estándar o proporcionada por el usuario. Una vez que el IDE detecta que un complemento admite el archivo *MSSCCPRJ.SCC,* deja de insertar las cadenas "AuxPath" y "ProjName" en los archivos de solución y proyecto, y lee esas cadenas del archivo *MSSCCPRJ.SCC* en su lugar.

 Un complemento de control de código fuente que admita el *archivo MSSCCPRJ.SCC* debe cumplir las siguientes directrices:

- Solo puede haber un *archivo MSSCCPRJ.SCC* por directorio.

- Un *archivo MSSCCPRJ.SCC* puede contener "AuxPath" y "ProjName" para varios archivos que están bajo control de código fuente dentro de un directorio determinado.

- La cadena "AuxPath" no debe tener comillas dentro de ella. Puede tener comillas alrededor como delimitadores (por ejemplo, se puede usar un par de comillas dobles para indicar una cadena vacía). El IDE quitará todas las comillas de la cadena "AuxPath" cuando se lea desde el *archivo MSSCCPRJ.SCC.*

- Cadena "ProjName" en *MSSCCPRJ. El archivo SCC* debe coincidir exactamente con la cadena devuelta por la `SccGetProjPath` función. Si la cadena devuelta por la función tiene comillas alrededor, la cadena del archivo *MSSCCPRJ.SCC* debe tener comillas alrededor y viceversa.

- Se crea o actualiza un archivo *MSSCCPRJ.SCC* cada vez que se coloca un archivo bajo control de código fuente.

- Si se elimina un archivo *MSSCCPRJ.SCC,* un proveedor debe volver a generarlo la próxima vez que realice una operación de control de código fuente relativa a ese directorio.

- Un *archivo MSSCCPRJ.SCC* debe seguir estrictamente el formato definido.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Ilustración de MSSCCPRJ. Formato de archivo SCC
 A continuación se muestra un ejemplo del formato de archivo *MSSCCPRJ.SCC* (los números de línea solo se proporcionan como guía y no deben incluirse en el cuerpo del archivo):

- [Línea 1] `SCC = This is a Source Code Control file`

- [Línea 2]

- [Línea 3] `[TestApp.sln]`

- [Línea 4] `SCC_Aux_Path = "\\server\vss\"`

- [Línea 5] `SCC_Project_Name = "$/TestApp"`

- [Línea 6]

- [Línea 7] `[TestApp.csproj]`

- [Línea 8] `SCC_Aux_Path = "\\server\vss\"`

- [Línea 9] `SCC_Project_Name = "$/TestApp"`

 La primera línea indica el propósito del archivo y actúa como firma para todos los archivos de este tipo. Esta línea debe aparecer exactamente como esta en todos los *archivos MSSCCPRJ.SCC:*

 `SCC = This is a Source Code Control file`

 En la sección siguiente se detalla la configuración de cada archivo, marcada por el nombre de archivo entre corchetes. Esta sección se repite para cada archivo del que se realiza el seguimiento. Esta línea es un ejemplo de un nombre de archivo, es decir, `[TestApp.csproj]` . El IDE espera las dos líneas siguientes. Sin embargo, no define el estilo de los valores definidos. Las variables son `SCC_Aux_Path` y `SCC_Project_Name` .

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 No hay ningún delimitador final en esta sección. El nombre del archivo, así como todos los literales que aparecen en el archivo, se definen en el archivo de encabezado scc.h. Para obtener más información, vea [Cadenas usadas como claves para buscar un complemento de control de código fuente.](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)

## <a name="see-also"></a>Consulta también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [Cadenas usadas como claves para buscar un complemento de control de código fuente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
