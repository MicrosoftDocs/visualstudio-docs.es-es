---
title: Ficha de archivo de paginación, cuadro de diálogo de propiedades de proceso | Documentos de Microsoft
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62904112"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Pestaña Archivo de paginación (Cuadro de diálogo Propiedades del proceso)
Use la **archivo de paginación** pestaña para examinar el archivo de paginación de un proceso. Para mostrar el [cuadro de diálogo de propiedades de proceso](../debugger/process-properties-dialog-box.md), mover el foco a un [vista procesos](../debugger/processes-view.md) ventana. Seleccione cualquier nodo de proceso en el árbol y luego elija **propiedades** desde el **vista** menú.

 Las siguientes opciones están disponibles en el **archivo de paginación** pestaña:

|Entrada|Descripción|
|-----------|-----------------|
|**Bytes de archivo de paginación**|El número actual de páginas que este proceso está usando en el archivo de paginación. El archivo de paginación almacena las páginas de datos utilizado por el proceso, pero no contenidas en otros archivos. El archivo de paginación se usa por todos los procesos y la falta de espacio en el archivo de paginación puede provocar errores mientras se está ejecutando otros procesos.|
|**Bytes de archivo de paginación máximos**|El número máximo de páginas que este proceso ha usado en el archivo de paginación.|
|**Errores de página**|El número de errores de página por los subprocesos ejecutados en este proceso. Se produce un error de página cuando un subproceso hace referencia a una página de memoria virtual que no está en su espacio de trabajo en la memoria principal. Por lo tanto, la página no se recuperará desde el disco si se encuentra en la lista en espera y, por tanto, en la memoria principal, o si lo está usando otro proceso con el que se comparte la página.|