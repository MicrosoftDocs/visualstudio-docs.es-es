---
title: Establecer opciones de nombre de archivo de datos de rendimiento | Microsoft Docs
description: Obtenga más información sobre cómo puede cambiar cualquier parámetro de nomenclatura en la página General del cuadro de diálogo de propiedades de la sesión de rendimiento.
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 110199375aef4f4a1168c761a5dad9d77da215b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907010"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Procedimiento Establecer opciones de nombre de archivo de datos de rendimiento

De forma predeterminada, se guarda un archivo de generación de perfiles de datos (.*vsp*) mediante la siguiente sintaxis:

*Path\VSP-File\YYMMDD(N)* **.vsp**

Puede cambiar cualquier parámetro de nomenclatura en la página **General** del cuadro de diálogo de propiedades de la sesión de rendimiento.

|Parámetro|Descripción|
|-|-|
|*Ruta de acceso*|El directorio que contiene el informe. La ubicación predeterminada es la carpeta de soluciones o la ubicación predeterminada de los proyectos y soluciones del usuario.|
|*VSP-File*|El nombre del archivo de datos de generación de perfiles. El nombre predeterminado es el nombre de la solución o ejecutable del que se generan perfiles.|
|*YYMMDD*|Una marca de fecha que muestra el año, mes y día en que se recopilaron los datos de generación de perfiles.|
|*(N)*|Si existe más de un archivo de datos de generación de perfiles, se agrega un número incrementado al nombre de archivo entre paréntesis.|

## <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Para cambiar la sintaxis de nomenclatura de los archivos de datos de generación de perfiles de una sesión de rendimiento

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
