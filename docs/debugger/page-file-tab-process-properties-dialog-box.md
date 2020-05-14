---
title: Archivo de paginación (Pestaña), Propiedades del proceso (Cuadro de diálogo) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25dc3b0aca1b58c18ae4038540c14fc4dbfe4036
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62904112"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Pestaña Archivo de paginación (Cuadro de diálogo Propiedades del proceso)
Use la pestaña **Archivo de paginación** para examinar el archivo de paginación de un proceso. Para mostrar el [Cuadro de diálogo Propiedades del proceso](../debugger/process-properties-dialog-box.md), mueva el foco a una ventana de la [Vista Procesos](../debugger/processes-view.md). Seleccione cualquier nodo de proceso del árbol y luego **Propiedades** en el menú **Vista**.

 En la pestaña **Archivo de paginación** están disponibles los valores siguientes:

|Entrada|Descripción|
|-----------|-----------------|
|**Bytes de archivo de paginación**|Número actual de páginas que este proceso está usando en el archivo de paginación. El archivo de paginación almacena las páginas de datos que usa el proceso pero que no están incluidas en otros archivos. Todos los procesos usan el archivo de paginación; la falta de espacio en él puede producir errores mientras se ejecutan otros procesos.|
|**Bytes de archivo de paginación máximos**|Número máximo de páginas del archivo de paginación que este proceso ha usado.|
|**Errores de página**|Número de errores de página de los subprocesos que se ejecutan en este proceso. Cuando un subproceso hace referencia a una página de memoria virtual que no está en su espacio de trabajo de la memoria principal, se produce un error de página. Así, la página no se recupera del disco si se encuentra en la lista de espera y, por tanto, aún en la memoria principal, o si está siendo usada por otro proceso con el que se comparte la página.|