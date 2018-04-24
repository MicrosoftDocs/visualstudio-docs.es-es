---
title: Pestaña archivo de paginación, cuadro de diálogo de propiedades de proceso | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 624be76badf8d57b060198c2ee910ead17b5efcb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Pestaña Archivo de paginación (Cuadro de diálogo Propiedades del proceso)
Use la **archivo de paginación** pestaña para examinar el archivo de paginación de un proceso. Para mostrar la [cuadro de diálogo de propiedades de proceso](../debugger/process-properties-dialog-box.md), mover el foco a un [vista procesos](../debugger/processes-view.md) ventana. Seleccione cualquier nodo de proceso en el árbol y después elija **propiedades** desde el **vista** menú.  
  
 Las siguientes opciones están disponibles en la **archivo de paginación** ficha:  
  
|Entrada|Descripción|  
|-----------|-----------------|  
|**Bytes del archivo de paginación**|El número actual de páginas que este proceso está usando en el archivo de paginación. El archivo de paginación almacena las páginas de datos utilizada por el proceso, pero no contenidas en otros archivos. El archivo de paginación se usa por todos los procesos y la falta de espacio en el archivo de paginación puede provocar errores mientras se están ejecutando otros procesos.|  
|**Bytes de archivo de página máximos**|El número máximo de páginas que este proceso ha usado en el archivo de paginación.|  
|**Errores de página**|El número de errores de página por los subprocesos ejecutados en este proceso. Se produce un error de página cuando un subproceso hace referencia a una página de memoria virtual que no está en su espacio de trabajo en la memoria principal. Por lo tanto, la página no se recuperará desde el disco si está en la lista de espera y, por lo que ya se encuentran en la memoria principal, o si la está usando otro proceso con el que se comparte la página.|