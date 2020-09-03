---
title: 'Área de prueba 6: eliminar | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3ffe786b5bc5f6d0bb0233fbb431988e0145611d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155931"
---
# <a name="test-area-6-delete"></a>Área de prueba 6: Eliminar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Este área de prueba del complemento de control de código fuente cubre las acciones de eliminación.  
  
 El control de código fuente responde a las acciones de eliminación en **Explorador de soluciones**.  
  
 A continuación se muestra una lista de los elementos que se pueden eliminar:  
  
- Archivos  
  
- Carpetas  
  
- Proyecto  
  
  Dependiendo del tipo de proyecto, puede que tenga la opción de **quitar** el proyecto (deja los archivos en disco) o **eliminar** el proyecto (quita los archivos en el disco). Cualquier acción quita el proyecto o el elemento de **Explorador de soluciones**.  
  
## <a name="expected-behavior"></a>Comportamiento esperado  
 El comportamiento esperado para los casos de prueba en el área de prueba de eliminación es:  
  
- El elemento eliminado ya no está visible en **Explorador de soluciones**.  
  
- El elemento primario del proyecto o elemento eliminado se desprotege según sea necesario (posiblemente con un símbolo del sistema).  
  
- Después de eliminar un elemento desprotegido o agregado, no aparece en la ventana **protecciones pendientes** .  
  
- El elemento todavía existe en el almacén de control de código fuente, incluso después de la eliminación, y se debe purgar manualmente.  
  
|Acción|Pasos de prueba|Resultados esperados que se van a comprobar|  
|------------|----------------|--------------------------------|  
|Eliminar un proyecto de cliente|1. cree un proyecto de cliente.<br />2. Agregue la solución al control de código fuente.<br />3. quitar todo el proyecto de la solución|Comportamiento esperado común.|  
|Eliminar un archivo vacío|1. cree un proyecto de cliente.<br />2. Agregue un archivo de cero bytes al proyecto.<br />3. agregar la solución al control de código fuente.<br />4. Seleccione el archivo, elimínelo.|Comportamiento esperado común.|  
|Eliminar una carpeta con un archivo|1. cree una solución de proyecto único.<br />2. Agregue una carpeta.<br />3. Agregue un archivo a la carpeta.<br />4. Agregue la solución al control de código fuente.<br />5. Consulte el proyecto para evitar los mensajes.<br />6. Elimine la carpeta.|Comportamiento esperado común.|  
|Eliminar un proyecto web del sistema de archivos|1. crear un proyecto Web de sistema de archivos (use el botón Examinar para especificar una ruta de acceso UNC).<br />2. Agregue la solución al control de código fuente.<br />3. Quite todo el proyecto de la solución.<br />4. Repita los pasos 1 a 3 para un proyecto Web local (ejercita diferentes rutas de acceso a través del código, pero tiene la misma interfaz externa y el mismo comportamiento).|Comportamiento esperado común.|  
|Eliminar un archivo de un proyecto web del sistema de archivos|1. cree un proyecto Web de sistema de archivos.<br />2. Agregue la solución al control de código fuente.<br />3. eliminar un archivo del proyecto.<br />4. Repita los pasos 1 a 3 para un proyecto Web local (ejercita diferentes rutas de acceso a través del código, pero tiene la misma interfaz externa y el mismo comportamiento).|Comportamiento esperado común.|  
  
## <a name="see-also"></a>Consulte también  
 [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
