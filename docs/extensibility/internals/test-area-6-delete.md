---
title: 'Zona de prueba 6: Eliminar á Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9902ab9d1cb9c28ddf67b83590a4cccd5f6562f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704507"
---
# <a name="test-area-6-delete"></a>Área de prueba 6: eliminar
Este área de prueba del complemento de control de código fuente cubre las acciones de eliminación.

 El control de código fuente responde a las acciones de eliminación en el Explorador de **soluciones.**

 A continuación se muestra una lista de elementos que se pueden eliminar:

- Archivos

- Carpetas

- proyecto

  Según el tipo de proyecto, es posible que tenga la opción **Quitar** el proyecto (deja los archivos en el disco) o **Eliminar** el proyecto (elimina los archivos en el disco). Cualquiera de las acciones quita el proyecto o el elemento del Explorador de **soluciones**.

## <a name="expected-behavior"></a>Comportamiento esperado
 El comportamiento esperado para los casos de prueba en el área de prueba de eliminación es:

- El elemento eliminado ya no está visible en el Explorador de **soluciones.**

- El elemento primario del proyecto o elemento eliminado se desprotege según sea necesario (posiblemente con un mensaje.)

- Después de eliminar un elemento desprotegido o agregado, NO aparece en la ventana **Checkins pendientes.**

- El elemento todavía existe dentro del almacén de control de código fuente, incluso después de la eliminación, y debe purgarse manualmente.

|Acción|Pasos de prueba|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Eliminar un proyecto de cliente|1. Cree un proyecto de cliente.<br />2. Agregue la solución al control de código fuente.<br />3. Retire todo el proyecto de la solución|Comportamiento esperado común.|
|Eliminar un archivo vacío|1. Cree un proyecto de cliente.<br />2. Agregue un archivo de cero bytes al proyecto.<br />3. Agregue la solución al control de código fuente.<br />4. Seleccione el archivo, elimínelo.|Comportamiento esperado común.|
|Eliminar una carpeta con un archivo|1. Cree una solución de proyecto único.<br />2. Agregue una carpeta.<br />3. Agregue un archivo a la carpeta.<br />4. Agregue la solución al control de código fuente.<br />5. Echa un vistazo al proyecto para evitar mensajes.<br />6. Elimine la carpeta.|Comportamiento esperado común.|
|Eliminar un proyecto web del sistema de archivos|1. Cree un proyecto Web del sistema de archivos (utilice el botón Examinar para especificar una ruta UNC).<br />2. Agregue la solución al control de código fuente.<br />3. Retire todo el proyecto de la solución.<br />4. Repita los pasos del 1 al 3 para un proyecto Web local (ejerce diferentes rutas de acceso a través del código, pero tiene la misma interfaz externa y comportamiento).|Comportamiento esperado común.|
|Eliminar un archivo de un proyecto web del sistema de archivos|1. Cree un proyecto Web del sistema de archivos.<br />2. Agregue la solución al control de código fuente.<br />3. Elimine un archivo del proyecto.<br />4. Repita los pasos del 1 al 3 para un proyecto Web local (ejerce diferentes rutas de acceso a través del código, pero tiene la misma interfaz externa y comportamiento).|Comportamiento esperado común.|

## <a name="see-also"></a>Vea también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
