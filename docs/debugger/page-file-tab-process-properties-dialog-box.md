---
title: Archivo de paginación (Pestaña), Propiedades del proceso (Cuadro de diálogo) | Microsoft Docs
description: Use la pestaña Archivo de paginación de Propiedades del proceso para examinar el archivo de paginación de un proceso. En este artículo se describe la configuración disponible.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b762fc95d510d5b99a2d4f8f939ef1801b5e70cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891571"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Pestaña Archivo de paginación (Cuadro de diálogo Propiedades del proceso)
Use la pestaña **Archivo de paginación** para examinar el archivo de paginación de un proceso. Para mostrar el [Cuadro de diálogo Propiedades del proceso](../debugger/process-properties-dialog-box.md), mueva el foco a una ventana de la [Vista Procesos](../debugger/processes-view.md). Seleccione cualquier nodo de proceso del árbol y luego **Propiedades** en el menú **Vista**.

 En la pestaña **Archivo de paginación** están disponibles los valores siguientes:

|Entrada|Descripción|
|-----------|-----------------|
|**Bytes de archivo de paginación**|Número actual de páginas que este proceso está usando en el archivo de paginación. El archivo de paginación almacena las páginas de datos que usa el proceso pero que no están incluidas en otros archivos. Todos los procesos usan el archivo de paginación; la falta de espacio en él puede producir errores mientras se ejecutan otros procesos.|
|**Bytes de archivo de paginación máximos**|Número máximo de páginas del archivo de paginación que este proceso ha usado.|
|**Errores de página**|Número de errores de página de los subprocesos que se ejecutan en este proceso. Cuando un subproceso hace referencia a una página de memoria virtual que no está en su espacio de trabajo de la memoria principal, se produce un error de página. Así, la página no se recupera del disco si se encuentra en la lista de espera y, por tanto, aún en la memoria principal, o si está siendo usada por otro proceso con el que se comparte la página.|