---
title: Archivo de paginación (Pestaña), Propiedades del proceso (Cuadro de diálogo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 24fdba37be2373623d94f03e45dc5e8a41a74b84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192720"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Pestaña Archivo de paginación (Cuadro de diálogo Propiedades del proceso)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use la pestaña **Archivo de paginación** para examinar el archivo de paginación de un proceso. Para mostrar el [Cuadro de diálogo Propiedades del proceso](../debugger/process-properties-dialog-box.md), mueva el foco a una ventana de la [Vista Procesos](../debugger/processes-view.md). Seleccione cualquier nodo de proceso del árbol y luego **Propiedades** en el menú **Vista**.  
  
 En la pestaña **Archivo de paginación** están disponibles los valores siguientes:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Bytes de archivo de paginación**|Número actual de páginas que este proceso está usando en el archivo de paginación. El archivo de paginación almacena las páginas de datos que usa el proceso pero que no están incluidas en otros archivos. Todos los procesos usan el archivo de paginación; la falta de espacio en él puede producir errores mientras se ejecutan otros procesos.|  
|**Bytes de archivo de paginación máximos**|Número máximo de páginas del archivo de paginación que este proceso ha usado.|  
|**Errores de página**|Número de errores de página de los subprocesos que se ejecutan en este proceso. Cuando un subproceso hace referencia a una página de memoria virtual que no está en su espacio de trabajo de la memoria principal, se produce un error de página. Así, la página no se recupera del disco si se encuentra en la lista de espera y, por tanto, aún en la memoria principal, o si está siendo usada por otro proceso con el que se comparte la página.|
