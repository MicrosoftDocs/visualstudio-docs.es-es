---
title: MSSCCPRJ. Archivo de control de código fuente | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a04429bafb7da0b3d4922905bd712e82ba16a4ba
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736153"
---
# <a name="mssccprjscc-file"></a>Archivo MSSCCPRJ.SCC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando se coloca una solución de Visual Studio o proyecto bajo control de código fuente mediante el IDE, el IDE recibe dos piezas clave de información desde el complemento en forma de cadenas de control de código fuente. Estas cadenas, "AuxPath" y "Nombre_proyecto", son opacas para el IDE, pero se usan por el complemento para buscar la solución o proyecto bajo control de versiones. El IDE normalmente obtiene estas cadenas de la primera vez mediante una llamada a la [SccGetProjPath](../extensibility/sccgetprojpath-function.md), y, a continuación, guarda en el archivo de solución o proyecto para las futuras llamadas a la [SccOpenProject](../extensibility/sccopenproject-function.md). Cuando se insertan en los archivos de solución y proyecto, las cadenas "AuxPath" y "Nombre_proyecto" no se actualizan automáticamente cuando un usuario, ramas, las bifurcaciones, o copia los archivos de solución y proyecto que se encuentran en el control de versiones. Para asegurarse de que los archivos de solución y proyecto señalan a su ubicación correcta en el control de versiones, los usuarios deben actualizar manualmente las cadenas. Dado que las cadenas están diseñadas para ser opaca, no siempre puede claro cómo debe actualizarse.  
  
 El complemento de control de código fuente puede evitar este problema almacenando las cadenas "AuxPath" y "Nombre_proyecto" en un archivo especial denominado el MSSCCPRJ. Archivo de control de código fuente. Es un archivo local del cliente que posee y mantiene el complemento. Este archivo nunca se coloca bajo control de código fuente, pero se genera mediante el complemento para todos los directorios que contiene los archivos controlados por código fuente. Para determinar qué archivos son archivos de solución y proyecto de Visual Studio, un complemento de control de código fuente puede comparar las extensiones de archivo con una lista estándar o proporcionado por el usuario. Una vez que el IDE detecta que un complemento es compatible con la MSSCCPRJ. Archivo de control de código fuente, deja de incrustar el "AuxPath" y las cadenas "Nombre_proyecto" en la solución y archivos de proyecto y lo lee estas cadenas de la MSSCCPRJ. Control de código fuente de archivos en su lugar.  
  
 Un control de código fuente complemento que admite el MSSCCPRJ. Archivo de control de código fuente debe cumplir las siguientes directrices:  
  
-   Solo puede haber un MSSCCPRJ. Archivo de control de código fuente por directorio.  
  
-   Un MSSCCPRJ. Archivo de control de código fuente puede contener la "AuxPath" y "Nombre_proyecto" para varios archivos que están bajo control de código fuente dentro de un directorio determinado.  
  
-   La cadena "AuxPath" no debe tener comillas dentro de él. Se le permite tener comillas como delimitadores (por ejemplo, un par de comillas dobles puede utilizarse para indicar una cadena vacía). El IDE eliminará todas las ofertas de la cadena "AuxPath" cuando se lee desde el MSSCCPRJ. Archivo de control de código fuente.  
  
-   La cadena "Nombre_proyecto" en el MSSCCPRJ. Archivo de control de código fuente debe coincidir con exactamente la cadena devuelta desde el `SccGetProjPath` función. Si la cadena devuelta por la función tiene comillas alrededor de ella, la cadena en el MSSCCPRJ. Archivo de control de código fuente debe tener comillas alrededor de ella y viceversa.  
  
-   Un MSSCCPRJ. Archivo de control de código fuente se crea o actualiza cada vez que se coloca un archivo bajo control de código fuente.  
  
-   Si está un MSSCCPRJ. Se elimina el archivo de control de código fuente, un proveedor debe regenerar la próxima vez que realiza una operación de control de código fuente relativos a ese directorio.  
  
-   Un MSSCCPRJ. Archivo de SCC estrictamente debe seguir el formato definido.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Ver una ilustración de la MSSCCPRJ. Formato de archivo de control de código fuente  
 Siguiente es un ejemplo de la MSSCCPRJ. Formato de archivo de control de código fuente (los números de línea solo se proporcionan como guía y no deben incluirse en el cuerpo del archivo):  
  
 [Línea 1] `SCC = This is a Source Code Control file`  
  
 [Línea 2]  
  
 [Línea 3] `[TestApp.sln]`  
  
 [Línea 4] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Línea 5] `SCC_Project_Name = "$/TestApp"`  
  
 [La línea 6]  
  
 [Línea 7] `[TestApp.csproj]`  
  
 [Línea 8] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Línea 9] `SCC_Project_Name = "$/TestApp"`  
  
 La primera línea indica el propósito del archivo y actúa como la firma para todos los archivos de este tipo. Esta línea debe aparecer exactamente igual en todos los MSSCCPRJ. Archivos CCF:  
  
 `SCC = This is a Source Code Control file`  
  
 Lo que sigue es una sección de configuración para cada archivo, marcados con el nombre de archivo incluido entre corchetes. En esta sección se repite para cada archivo que se está realizando un seguimiento. Esta línea es un ejemplo de un nombre de archivo, es decir, `[TestApp.csproj]`. El IDE se espera que las dos líneas siguientes. Sin embargo, no es así, definir el estilo de los valores definidos. Las variables son `SCC_Aux_Path` y `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 No hay ningún delimitador de fin a esta sección. El nombre de archivo, así como todos los literales que aparecen en el archivo, se definen en el archivo de encabezado scc.h. Para obtener más información, consulte [cadenas utilizadas como claves para buscar un complemento de Control de código fuente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [Cadenas utilizadas como claves para buscar un complemento de control de código fuente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)

