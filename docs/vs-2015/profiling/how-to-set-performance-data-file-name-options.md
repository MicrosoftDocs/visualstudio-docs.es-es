---
title: 'Cómo: establecer opciones de nombre de archivo de datos de rendimiento | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71ac053a24b3f765a58fc050ceec84115e1a4e3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548400"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Cómo: establecer opciones de nombre de archivo de datos de rendimiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

De forma predeterminada, se guarda un archivo de generación de perfiles de datos (.vsp) mediante la siguiente sintaxis:  
  
 *Path\VSP-File\YYMMDD(N)* **.vsp**  
  
 Puede cambiar cualquier parámetro de nomenclatura en la página General del cuadro de diálogo de propiedades de la sesión de rendimiento.  
  
 **Requisitos**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
|Elemento Syntax|Descripción|  
|-|-|  
|*Ruta de acceso*|El directorio que contiene el informe. La ubicación predeterminada es la carpeta de soluciones o la ubicación predeterminada de los proyectos y soluciones del usuario.|  
|*VSP-File*|El nombre del archivo de datos de generación de perfiles. El nombre predeterminado es el nombre de la solución o ejecutable del que se generan perfiles.|  
|*YYMMDD*|Una marca de fecha que muestra el año, mes y día en que se recopilaron los datos de generación de perfiles.|  
|*(N)*|Si existe más de un archivo de datos de generación de perfiles, se agrega un número incrementado al nombre de archivo entre paréntesis.|  
  
### <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Para cambiar la sintaxis de nomenclatura de los archivos de datos de generación de perfiles de una sesión de rendimiento  
  
1. En el **Explorador de rendimiento**, haga clic con el botón derecho en el nombre de la sesión de rendimiento y, después, haga clic en **Propiedades**.  
  
2. Haga clic en **General**.  
  
3. En **Informe**, cambie cualquiera de las siguientes opciones:  
  
    |NOMBRE|Descripción|  
    |-|-|  
    |**Ubicación del informe**|Especifique un directorio para almacenar los archivos de datos de generación de perfiles.|  
    |**Nombre del informe**|Especifique un nombre base para los archivos.|  
    |**Agregar nuevos informes a la sesión automáticamente**|Active la casilla para agregar automáticamente el archivo de datos a la sesión de rendimiento.|  
    |**Anexar un número incremental a informes generados**|Active la casilla para agregar un número incremental al nombre de archivo cuando exista más de un archivo con el mismo nombre. Desactive la casilla para sobrescribir un archivo existente.|  
    |**Usar una marca de tiempo para el número**|Active la casilla para agregar una fecha al nombre de archivo.|
