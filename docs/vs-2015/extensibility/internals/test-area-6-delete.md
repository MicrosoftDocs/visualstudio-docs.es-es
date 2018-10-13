---
title: 'Área de prueba 6: Eliminar | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f3e03ea9985840d20c812f56d7a0f9cae66420cc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49261821"
---
# <a name="test-area-6-delete"></a>Área de prueba 6: eliminar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta área de prueba de complemento de control de código fuente trata las acciones de eliminación.  
  
 Para eliminar las acciones en que responde el control de código fuente **el Explorador de soluciones**.  
  
 Siguiente es una lista de elementos que se pueden eliminar:  
  
-   Archivos  
  
-   Carpetas  
  
-   Proyecto  
  
 Según el tipo de proyecto, tendrá la opción de **quitar** el proyecto (deja los archivos en disco) o **eliminar** el proyecto (elimina los archivos en disco). Cualquier acción quita el proyecto o elemento de **el Explorador de soluciones**.  
  
## <a name="expected-behavior"></a>Comportamiento esperado  
 Es el comportamiento esperado para los casos de prueba en el área de prueba de eliminación:  
  
-   Elemento eliminado ya no está visible dentro de **el Explorador de soluciones**.  
  
-   El elemento primario del proyecto eliminado o elemento está desprotegido según sea necesario (posiblemente con un símbolo del sistema.)  
  
-   Después de eliminar un checked out o elemento agregado, no aparecen en la **protecciones pendientes** ventana.  
  
-   El elemento aún existe en el almacén de control de código fuente, incluso después de la eliminación y se debe purgar manualmente.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Eliminar un proyecto de cliente|1.  Cree un proyecto de cliente.<br />2.  Agregue la solución al control de código fuente.<br />3.  Quitar todo el proyecto de solución|Comportamiento esperado común.|  
|Eliminar un archivo vacío|1.  Cree un proyecto de cliente.<br />2.  Agregue un archivo de cero bytes al proyecto.<br />3.  Agregue la solución al control de código fuente.<br />4.  Seleccione el archivo, elimínelo.|Comportamiento esperado común.|  
|Eliminar una carpeta con un solo archivo|1.  Crear solución de proyecto único.<br />2.  Agregue una carpeta.<br />3.  Agregue un archivo a la carpeta.<br />4.  Agregue la solución al control de código fuente.<br />5.  Extraer del repositorio el proyecto para evitar mensajes.<br />6.  Elimine la carpeta.|Comportamiento esperado común.|  
|Eliminar un proyecto Web de sistema de archivos|1.  Cree un proyecto Web de sistema de archivos (use el botón Examinar para especificar una ruta de acceso UNC).<br />2.  Agregue la solución al control de código fuente.<br />3.  Quitar todo el proyecto de la solución.<br />4.  Repita los pasos del 1 al 3 para un proyecto Web local (ejercita diferentes rutas de acceso a través del código, pero tiene la misma interfaz externa y el comportamiento).|Comportamiento esperado común.|  
|Eliminar un archivo de un proyecto Web de sistema de archivos|1.  Crear un proyecto Web de sistema de archivos.<br />2.  Agregue la solución al control de código fuente.<br />3.  Eliminar un archivo del proyecto.<br />4.  Repita los pasos del 1 al 3 para un proyecto Web local (ejercita diferentes rutas de acceso a través del código, pero tiene la misma interfaz externa y el comportamiento).|Comportamiento esperado común.|  
  
## <a name="see-also"></a>Vea también  
 [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

