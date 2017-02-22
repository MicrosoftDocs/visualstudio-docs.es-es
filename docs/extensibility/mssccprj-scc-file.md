---
title: "MSSCCPRJ. Archivo de control de c&#243;digo fuente | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSCCPRJ de los complementos de control de código fuente. Archivo de control de código fuente"
  - "MSSCCPRJ. Archivo de control de código fuente"
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# MSSCCPRJ. Archivo de control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se coloca una solución de Visual Studio o proyecto bajo control de código fuente con el IDE, el IDE recibe dos fragmentos de información clave desde el control de código fuente en forma de cadenas. Estas cadenas, "AuxPath" y "Nombreproyecto" son opacas para el IDE, pero se utilizan por el complemento para buscar la solución o proyecto bajo control de versiones. El IDE normalmente obtiene estas cadenas de la primera vez llamando a la [SccGetProjPath](../extensibility/sccgetprojpath-function.md), y, a continuación, guarda en el archivo de solución o proyecto para las futuras llamadas a la [SccOpenProject](../extensibility/sccopenproject-function.md). Cuando se incrustan en los archivos de solución y proyecto, las cadenas "AuxPath" y "Nombreproyecto" no se actualizan automáticamente cuando un usuario bifurcaciones bifurcaciones, o copia los archivos de solución y proyecto de control de versiones. Para asegurarse de que los archivos de solución y proyecto señalan a su ubicación correcta en el control de versiones, los usuarios deben actualizar manualmente las cadenas. Dado que las cadenas están diseñadas para ser opaco, no siempre es claro cómo debe actualizarse.  
  
 El complemento de control de código fuente puede evitar este problema almacenando las cadenas "AuxPath" y "Nombreproyecto" en un archivo especial denominado el MSSCCPRJ. Archivo de control de código fuente. Es un archivo local del cliente que posee y mantiene el complemento. Este archivo nunca está sometido a control de código fuente, pero se genera mediante el complemento para todos los directorios que contiene los archivos de control de código fuente. Para determinar qué archivos son archivos de solución y proyecto de Visual Studio, un complemento de control de código fuente puede comparar las extensiones de archivo con una lista estándar o proporcionados por el usuario. Una vez que el IDE detecta que un complemento es compatible con la MSSCCPRJ. Archivo SCC, deja de incrustar lo "AuxPath" y "Nombreproyecto" cadenas en la solución y archivos de proyecto y lo lee esas cadenas de la MSSCCPRJ. Control de código fuente de archivos en su lugar.  
  
 Un control de código fuente complemento que admite el MSSCCPRJ. Archivo de control de código fuente debe cumplir las siguientes directrices:  
  
-   Sólo puede haber un MSSCCPRJ. Archivo de control de código fuente por directorio.  
  
-   Un MSSCCPRJ. Archivo de control de código fuente puede contener el "AuxPath" y "Nombreproyecto" para varios archivos que están bajo control de código fuente en un directorio determinado.  
  
-   La cadena "AuxPath" no debe tener entre comillas dentro de él. Se le permite tener comillas como delimitadores \(por ejemplo, un par de comillas dobles puede utilizarse para indicar una cadena vacía\). El IDE quitará todas las ofertas de la cadena "AuxPath" cuando se lee desde el MSSCCPRJ. Archivo de control de código fuente.  
  
-   La cadena "Nombreproyecto" en la MSSCCPRJ. Archivo de control de código fuente debe coincidir con exactamente la cadena devuelta de la `SccGetProjPath` \(función\). Si la cadena devuelta por la función tiene comillas, la cadena en el MSSCCPRJ. Archivo de control de código fuente debe tener comillas alrededor de ella y viceversa.  
  
-   Un MSSCCPRJ. Archivo de control de código fuente se crea o se actualiza cada vez que se coloca un archivo bajo control de código fuente.  
  
-   Si está un MSSCCPRJ. Se elimina el archivo de control de código fuente, un proveedor debe regenerar la próxima vez que se realiza una operación de control de código fuente relativos a ese directorio.  
  
-   Un MSSCCPRJ. Archivo SCC estrictamente debe seguir el formato definido.  
  
## Una ilustración de la MSSCCPRJ. Formato de archivo de control de código fuente  
 Siguiente es un ejemplo de la MSSCCPRJ. Formato de archivo de control de código fuente \(los números de línea sólo se proporcionan como guía y no deben incluirse en el cuerpo del archivo\):  
  
 \[Línea 1\] `SCC = This is a Source Code Control file`  
  
 \[Línea 2\]  
  
 \[Línea 3\] `[TestApp.sln]`  
  
 \[Línea 4\] `SCC_Aux_Path = "\\server\vss\"`  
  
 \[Línea 5\] `SCC_Project_Name = "$/TestApp"`  
  
 \[Línea 6\]  
  
 \[Línea 7\] `[TestApp.csproj]`  
  
 \[Línea 8\] `SCC_Aux_Path = "\\server\vss\"`  
  
 \[Línea 9\] `SCC_Project_Name = "$/TestApp"`  
  
 La primera línea indica el propósito del archivo y actúa como la firma para todos los archivos de este tipo. Esta línea debe aparecer exactamente igual en todos los MSSCCPRJ. Archivos SCC:  
  
 `SCC = This is a Source Code Control file`  
  
 Lo que sigue es una sección de configuración para cada archivo, marcados con el nombre de archivo entre corchetes. En esta sección se repite para cada archivo que se está realizando un seguimiento. Esta línea es un ejemplo de un nombre de archivo, es decir, `[TestApp.csproj]`. El IDE se espera que las dos líneas siguientes. Sin embargo, no es así, definir el estilo de los valores definidos. Las variables son `SCC_Aux_Path` y `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 No hay ningún delimitador final a esta sección. El nombre de archivo, así como todos los literales que aparecen en el archivo, se definen en el archivo de encabezado scc.h. Para obtener más información, consulta [Cadenas que se utilizan como claves para buscar un Control de origen de complemento](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [Cadenas que se utilizan como claves para buscar un Control de origen de complemento](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)