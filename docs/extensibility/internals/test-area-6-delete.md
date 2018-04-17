---
title: 'Zona de ensayo 6: Eliminar | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97fc6ab9746e7ef2188c78dc77ec357f7d415a42
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="test-area-6-delete"></a>Probar el área 6: eliminar
Esta área de complemento de prueba de control de código fuente trata las acciones de eliminación.  
  
 Para eliminar las acciones en que responde el control de código fuente **el Explorador de soluciones**.  
  
 Aquí te mostramos una lista de elementos que se pueden eliminar:  
  
-   Archivos  
  
-   Carpetas  
  
-   Proyecto  
  
 Dependiendo del tipo de proyecto, tendrá la opción de **quitar** el proyecto (deja los archivos en disco) o **eliminar** el proyecto (quita los archivos en disco). Cualquiera de las acciones que quita el proyecto o elemento de **el Explorador de soluciones**.  
  
## <a name="expected-behavior"></a>Comportamiento esperado  
 El comportamiento esperado de los casos de prueba en la zona de ensayo de delete es:  
  
-   Elemento eliminado ya no sea visible en **el Explorador de soluciones**.  
  
-   El elemento primario del proyecto eliminado o elemento se desprotege según sea necesario (posiblemente con un símbolo del sistema.)  
  
-   Después de eliminar un checked out o elemento agregado, no aparecen en la **protecciones pendientes** ventana.  
  
-   El elemento aún existe en el almacén de control de código fuente, incluso después de la eliminación y se debe purgar manualmente.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Eliminar un proyecto de cliente|1.  Cree un proyecto de cliente.<br />2.  Agregar la solución al control de código fuente.<br />3.  Quitar todo el proyecto de solución|Comportamiento esperado común.|  
|Eliminar un archivo vacío|1.  Cree un proyecto de cliente.<br />2.  Agregue un archivo de cero bytes al proyecto.<br />3.  Agregar la solución al control de código fuente.<br />4.  Seleccione el archivo, elimínelo.|Comportamiento esperado común.|  
|Eliminar una carpeta con un archivo|1.  Crear solución de proyecto único.<br />2.  Agregar una carpeta.<br />3.  Agregar un archivo a la carpeta.<br />4.  Agregar la solución al control de código fuente.<br />5.  Desproteger el proyecto para evitar mensajes.<br />6.  Elimine la carpeta.|Comportamiento esperado común.|  
|Eliminar un proyecto Web de sistema de archivos|1.  Cree un proyecto Web del sistema de archivos (use el botón Examinar para especificar una ruta de acceso UNC).<br />2.  Agregar la solución al control de código fuente.<br />3.  Quite todo el proyecto de la solución.<br />4.  Repita los pasos del 1 al 3 para un proyecto Web local (ejercicios de diferentes rutas de acceso a través del código, pero tiene la misma interfaz externa y el comportamiento).|Comportamiento esperado común.|  
|Eliminar un archivo de un proyecto Web de sistema de archivos|1.  Crear un proyecto Web de sistema de archivos.<br />2.  Agregar la solución al control de código fuente.<br />3.  Elimine un archivo del proyecto.<br />4.  Repita los pasos del 1 al 3 para un proyecto Web local (ejercicios de diferentes rutas de acceso a través del código, pero tiene la misma interfaz externa y el comportamiento).|Comportamiento esperado común.|  
  
## <a name="see-also"></a>Vea también  
 [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)