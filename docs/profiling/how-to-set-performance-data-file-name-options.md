---
title: "C&#243;mo: Establecer opciones de nombre de archivo de datos de generaci&#243;n de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Establecer opciones de nombre de archivo de datos de generaci&#243;n de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

De forma predeterminada, para guardar un archivo de datos de generación de perfiles \(.vsp\) se utiliza la sintaxis siguiente:  
  
 *Path\\VSP\-File\\YYMMDD\(N\)* **.vsp**  
  
 Puede cambiar cualquier parámetro de denominación en la página General del cuadro de diálogo de propiedades de la sesión de rendimiento.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
|||  
|-|-|  
|*Path*|Directorio que contiene el informe.  La ubicación predeterminado es la carpeta de soluciones o la ubicación predeterminado para los proyectos y las soluciones del usuario.|  
|*VSP\-File*|Nombre del archivo de datos de generación de perfiles.  El nombre predeterminado es el nombre de la solución o aplicación ejecutable para la que se generan perfiles.|  
|*YYMMDD*|Marca de fecha que muestra el año, mes y día que se recolectaron los datos para la generación de perfiles.|  
|*\(N\)*|Si existe más de un archivo de datos de generación de perfiles, se agrega un número incrementado al nombre de archivo entre paréntesis.|  
  
### Para cambiar la sintaxis de la denominación de los archivos de datos de generación de perfiles de una sesión de rendimiento  
  
1.  En el **Explorador de rendimiento**, haga clic con el botón secundario en el nombre de la sesión de rendimiento y, a continuación, haga clic en **Propiedades**.  
  
2.  Haga clic en **General**.  
  
3.  Bajo **Informe**, cambie cualquiera de los valores siguientes:  
  
    |||  
    |-|-|  
    |**Ubicación del informe**|Especifique un directorio para almacenar los archivos de datos de generación de perfiles.|  
    |**Nombre del informe**|Especifique un nombre base para los archivos.|  
    |**Agregar nuevos informes a la sesión automáticamente**|Active la casilla para agregar el archivo de datos a la sesión de rendimiento automáticamente.|  
    |**Anexar un número para incrementar a los informes generados**|Active la casilla para agregar un número creciente al nombre de archivo cuando exista más de un archivo del mismo nombre.  Desactive la casilla para sobrescribir un archivo existente.|  
    |**Usar una marca de tiempo para el número**|Active la casilla para agregar una marca de fecha al nombre de archivo.|