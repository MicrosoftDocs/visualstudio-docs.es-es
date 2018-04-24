---
title: 'Cómo: establecer opciones de nombre de archivo de datos de rendimiento | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0687b4f56906aeca0866f8d5d6ad7d329bb84df6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-set-performance-data-file-name-options"></a>Cómo: establecer opciones de nombre de archivo de datos de rendimiento

De forma predeterminada, se guarda un archivo de generación de perfiles de datos (.vsp) mediante la siguiente sintaxis:

*Path\VSP-File\YYMMDD(N)* **.vsp**

Puede cambiar cualquier parámetro de nomenclatura en la página General del cuadro de diálogo de propiedades de la sesión de rendimiento.

|||
|-|-|
|*Path*|El directorio que contiene el informe. La ubicación predeterminada es la carpeta de soluciones o la ubicación predeterminada de los proyectos y soluciones del usuario.|
|*VSP-File*|El nombre del archivo de datos de generación de perfiles. El nombre predeterminado es el nombre de la solución o ejecutable del que se generan perfiles.|
|*YYMMDD*|Una marca de fecha que muestra el año, mes y día en que se recopilaron los datos de generación de perfiles.|
|*(N)*|Si existe más de un archivo de datos de generación de perfiles, se agrega un número incrementado al nombre de archivo entre paréntesis.|

## <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Para cambiar la sintaxis de nomenclatura de los archivos de datos de generación de perfiles de una sesión de rendimiento

1. En el **Explorador de rendimiento**, haga clic con el botón derecho en el nombre de la sesión de rendimiento y, después, haga clic en **Propiedades**.

2. Haga clic en **General**.

3. En **Informe**, cambie cualquiera de las siguientes opciones:

    |||
    |-|-|
    |**Ubicación del informe**|Especifique un directorio para almacenar los archivos de datos de generación de perfiles.|
    |**Nombre del informe**|Especifique un nombre base para los archivos.|
    |**Agregar nuevos informes a la sesión automáticamente**|Active la casilla para agregar automáticamente el archivo de datos a la sesión de rendimiento.|
    |**Anexar un número incremental a informes generados**|Active la casilla para agregar un número incremental al nombre de archivo cuando exista más de un archivo con el mismo nombre. Desactive la casilla para sobrescribir un archivo existente.|
    |**Usar una marca de tiempo para el número**|Active la casilla para agregar una fecha al nombre de archivo.|