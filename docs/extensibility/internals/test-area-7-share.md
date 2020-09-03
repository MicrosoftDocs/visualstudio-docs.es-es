---
title: 'Área de prueba 7: compartir | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd4c48e94015d95f5e56d465cdbf98562108d3b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704405"
---
# <a name="test-area-7-share"></a>Área de prueba 7: Compartir
En este área de prueba se trata el uso compartido de elementos entre ubicaciones a través del comando **compartir** .

 Una operación hhare es la duplicación aparente de archivos y elementos de carpeta entre dos o más ubicaciones de una jerarquía de archivos de control de código fuente. La duplicación no se produce realmente en el servidor, pero el usuario ve el mismo archivo en dos o más ubicaciones especificadas. Cada vez que se realizan cambios en cualquiera de los elementos compartidos, esos cambios aparecen en todas las demás ubicaciones compartidas.

 Compartir en carpetas funciona si selecciona una carpeta con al menos un archivo bajo control de código fuente. El comando compartir está deshabilitado en las siguientes condiciones:

- Si la carpeta seleccionada es una carpeta vacía.

- Si hay una carpeta real, pero no contiene archivos de control de código fuente.

- Si hay una carpeta virtual, si los archivos bajo control de código fuente están en él o no.

- Si hay un proyecto Web de sitio remoto.

## <a name="command-menu-access"></a>Acceso al menú de comandos
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]En los casos de prueba se usan las siguientes rutas de menú del entorno de desarrollo integrado.

 Recurso compartido **:** -> **Source Control** -> **recurso compartido**de control de código fuente.

## <a name="expected-behavior"></a>Comportamiento esperado

- Archivo compartido aparece en la ubicación compartida.

- Ver el historial del almacén de versiones de control de código fuente muestra que los archivos están compartidos.

- La edición de un archivo compartido edita ambas ubicaciones del archivo.

## <a name="test-cases"></a>Casos de prueba
 Los siguientes son casos de prueba específicos para el área de prueba de uso compartido.

|Acción|Pasos de prueba|Resultados esperados que se van a comprobar|
|------------|----------------|--------------------------------|
|Compartir un archivo de un proyecto cargado bajo control de código fuente en otro proyecto cargado|1. cree un nuevo proyecto.<br />2. agregar un segundo proyecto a la solución.<br />3. cree un archivo en el segundo proyecto con un nombre que no esté en el primer proyecto.<br />4. Agregue la solución al control de código fuente.<br />5. Seleccione el primer proyecto.<br />6. Abrir cuadro de diálogo **compartir** (**File**  ->  recurso compartido de**control de código fuente**de archivo  ->  **Share**).<br />7. compartir el archivo del segundo proyecto con el primero.<br />8. acepte la **desprotección** si se le solicita.|Comportamiento esperado común.|
|Compartir un archivo de un proyecto a otro|1. cree un nuevo proyecto.<br />2. agréguelo al control de código fuente.<br />3. Cierre la solución.<br />4. crear un segundo proyecto (nueva solución).<br />5. agregar la solución al control de código fuente.<br />6. Seleccione el proyecto.<br />7. Abra el cuadro de diálogo **compartir** (**File**  ->  recurso compartido de**control de código fuente**de archivo  ->  **Share**).<br />8. comparta un archivo desde el proyecto agregado previamente al proyecto abierto.<br />9. acepte la **desprotección** si se le solicita.|Comportamiento esperado común.|
|Compartir un archivo que no forma parte del proyecto desde el control de código fuente en el proyecto cargado actualmente|1. cree un nuevo proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. agregar un archivo al control de código fuente que no forma parte del proyecto o de la solución.<br />4. Seleccione el proyecto y abra el cuadro de diálogo **compartir** (**File**  ->  recurso compartido de**control de código fuente**de archivo  ->  **Share**).<br />5. Seleccione un archivo en el cuadro de diálogo **compartir** que no exista en el proyecto o la solución actual y compártalo.<br />6. acepte la **desprotección** si se le solicita.|El almacén de control de código fuente ha realizado un get, por lo que el archivo está ahora en la ubicación local del proyecto.|
|Compartir archivos dentro del mismo proyecto en una carpeta diferente|1. Seleccione **Desproteger automáticamente** en **herramientas**  ->  **Opciones**  ->  **control de código fuente**.<br />2. cree un nuevo proyecto y agréguelo al control de código fuente.<br />3. Agregue una carpeta al proyecto.<br />4. Agregue un archivo a la carpeta y proteja la carpeta.<br />5. Seleccione la carpeta.<br />6. Abrir cuadro de diálogo **compartir** (**File**  ->  recurso compartido de**control de código fuente**de archivo  ->  **Share**).<br />7. compartir el archivo con la carpeta seleccionada.|Comportamiento esperado común.<br /><br /> La carpeta debe protegerse con un archivo en ella para que se pueda usar para el recurso compartido.|
|Compartir una carpeta en el proyecto cargado: recursivo|1. cree un nuevo proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Seleccione el proyecto.<br />4. Abra el cuadro de diálogo **compartir** (**File**  ->  recurso compartido de**control de código fuente**de archivo  ->  **Share**).<br />5. Seleccione una carpeta.<br />6. comparta la carpeta de forma recursiva en el proyecto.|Comportamiento esperado común.|
|Compartir varios archivos de un proyecto a otro|1. cree un nuevo proyecto con varios archivos en él.<br />2. Agregue la solución al control de código fuente.<br />3. Cierre la solución.<br />4. cree un nuevo proyecto en una nueva solución.<br />5. agregar la solución al control de código fuente.<br />6. Seleccione el proyecto.<br />7. Abra el cuadro de diálogo **compartir** (**File**  ->  recurso compartido de**control de código fuente**de archivo  ->  **Share**).<br />8. comparta varios archivos del proyecto creado anteriormente con el proyecto actualmente abierto.|Comportamiento esperado común.|

## <a name="see-also"></a>Vea también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
