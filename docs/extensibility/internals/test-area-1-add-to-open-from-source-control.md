---
title: 'Área de prueba 1: agregar To-Open desde el control de código fuente | Microsoft Docs'
description: Este área de prueba del complemento de control de código fuente cubre la colocación de soluciones o proyectos bajo control de código fuente y su recuperación desde el control de código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dbcbc197a610f7caf2a1641a291db18fcea9dbda
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898322"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Área de prueba 1: Incorporación y apertura desde el control de código fuente
Este área de prueba del complemento de control de código fuente cubre la colocación de soluciones o proyectos bajo control de código fuente y su recuperación desde el control de código fuente.

## <a name="command-menu-access"></a>Acceso al menú de comandos
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]En los casos de prueba se usan las siguientes rutas de menú del entorno de desarrollo integrado:

- En [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] , abra desde el control de código fuente: **archivo**, **abrir**,  / **solución** de proyecto; busque en la [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ubicación.

- Para otros complementos de control de código fuente, abra desde el control de código fuente: **archivo**, **control de código fuente**, **abrir desde el control de código fuente**.

- Agregar al control de código fuente: **archivo**, **control de código fuente**, **Agregar solución al archivo de control de código fuente**, **control de código fuente**, **Agregar proyectos seleccionados al control de código fuente**.

- Menú contextual (proyecto/solución), **Agregar solución al control de código fuente**.

- Agregar desde el control de código fuente: **archivo**, **control de código fuente**, **Agregar proyecto desde el control de código fuente**.

- Para [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] , agregar desde el control de código fuente también está disponible desde **archivo**, **Agregar**, **proyecto existente**; buscar en la [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ubicación.

  > [!NOTE]
  > En esta prueba se puede usar una ruta de acceso de un archivo local o un servidor de IIS local (servidor Web).

## <a name="expected-behavior"></a>Comportamiento esperado

- Para cada tipo de proyecto compatible, un usuario debe poder "Agregar a" y "abrir desde" el control de código fuente.

- Cuando se agrega un proyecto al control de código fuente, \<*ProjectName*> se crea un archivo. vspscc correspondiente (archivo de sugerencia de proyecto). Contiene la información de conexión y la lista de archivos de exclusión. No elimine este archivo porque contiene información específica del proyecto.

- Cuando se agrega una solución al control de código fuente, \<*SolutionName*> se crea un archivo. vssscc (triple) correspondiente. El archivo de texto contiene información de conexión y una lista de archivos de exclusión, similar al archivo de sugerencia del proyecto. Este archivo es temporal y solo existe en la base de datos de control de código fuente.

- Cuando una solución se abre desde el control de código fuente, un \<*SolutionName*> archivo. vsscc (Double S) que solo existe en la base de datos de control de código fuente, se crea localmente en un archivo temporal. Este archivo contiene la ruta de acceso de la carpeta de conexión de la solución al archivo de solución. Este archivo es temporal y la copia local se elimina cuando se completa la operación "abrir desde el control de código fuente".

- Después de agregar un proyecto al control de código fuente, puede realizar cualquier acción de control de código fuente en él (desproteger, obtener, etc.).

## <a name="test-cases"></a>Casos de prueba
 Los siguientes son casos de prueba específicos para el área de prueba agregar a o abrir desde control de código fuente.

### <a name="case-1a-add-solution-to-source-control"></a>Caso 1a: Adición de la solución al control de código fuente
 Este caso de prueba se centra en agregar soluciones al control de código fuente.

|Acción|Pasos de prueba|Resultados esperados que se van a comprobar|
|------------|----------------|--------------------------------|
|Agregar una solución que contenga un proyecto de cliente al control de código fuente|1. cree un proyecto de cliente.<br />2. agregar la solución al control de código fuente (**archivo**, **control de código fuente**, **Agregar solución al control de código fuente**).|La solución o el proyecto se agregó al control de código fuente.|
|Agregar una solución que contenga un sistema de archivos o un proyecto Web de IIS local al control de código fuente|1. crear un sistema de archivos o un proyecto Web de IIS local (use el botón Examinar para apuntar a la ubicación del proyecto; la ruta de acceso determina el tipo de proyecto web que se crea).<br />2. agregar la solución al control de código fuente (**archivo**, **control de código fuente**, **Agregar solución al control de código fuente**).|La solución o el proyecto se agregó al control de código fuente.|
|Agregar una solución que contenga un proyecto Web de sitio remoto al control de código fuente|1. cree un proyecto Web de sitio remoto.<br />2. agregar la solución al control de código fuente (**archivo**, **control de código fuente**, **Agregar solución al control de código fuente**).<br />3. Haga clic en **Aceptar** en el cuadro de diálogo Advertencia de acceso de FrontPage.|La solución se ha agregado al control de código fuente.<br /><br /> El proyecto de sitio remoto no está bajo control de código fuente. (Los proyectos de sitio remoto deben controlarse desde su propio servidor IIS).|
|Agregue una solución de proyecto única al control de código fuente mediante **Agregar proyectos seleccionados al control de código fuente**.|1. cree una solución de proyecto único.<br />2. agregar solo la solución al control de código fuente como una selección (**archivo**, **control de código fuente**, **Agregar proyectos seleccionados al control de código fuente**). Si este paso se realiza correctamente, continúe con el paso siguiente.<br />3. agregar un proyecto al control de código fuente como selección (**archivo**, **control de código fuente**, **Agregar proyectos seleccionados al control de código fuente**).<br />4. Haga clic en **sí** para agregar el proyecto a la misma ubicación.<br />5 **. Haga clic en** desproteger en el cuadro **de diálogo desproteger para editar** .|`Result from Step 2:`<br /><br /> El proyecto y todos los archivos del proyecto tienen un indicador de control de código fuente desprotegido y la información sobre herramientas muestra "no bajo control de código fuente".<br /><br /> `Result from Step 5:`<br /><br /> El archivo de proyecto y de solución se encuentran en la misma carpeta en el control de código fuente.|
|Cancelar la adición de una solución al control de código fuente|1. cree una solución de proyecto único.<br />2. intente agregar el proyecto y la solución al control de código fuente. Si este paso se realiza correctamente, continúe con el paso siguiente.<br />3. cancele cuando esté en el sistema de control de código fuente.|`Result from Step 2:`<br /><br /> El cuadro de diálogo establecer control de código fuente de ubicación del proyecto aparece una sola vez.<br /><br /> `Result from Step 3:`<br /><br /> Proyecto agregado cancelado, el proyecto o la solución no está bajo control de código fuente y todos los menús agregar a control de código fuente siguen estando disponibles.|

### <a name="case-1b-open-solution-from-source-control"></a>Caso 1B. Abrir solución desde el control de código fuente
 Este caso de prueba se centra en la apertura de soluciones desde el control de código fuente.

|Acción|Pasos de prueba|Resultados esperados que se van a comprobar|
|------------|----------------|--------------------------------|
|Abrir una solución que contiene un proyecto de cliente desde el control de código fuente|1. cree un proyecto de cliente.<br />2. Agregue la solución al control de código fuente.<br />3. Cierre la solución.<br />4. Abra la solución desde el control de código fuente a una nueva ubicación.|Solución/proyecto abierto desde el control de código fuente.|
|Abrir una solución que contenga un proyecto Web local o IIS desde el control de código fuente|1. cree un proyecto Web local o IIS.<br />2. Agregue la solución al control de código fuente.<br />3. Cierre la solución.<br />4. Abra la solución desde el control de código fuente a una nueva ubicación.|Solución/proyecto abierto desde el control de código fuente.|
|Abrir una solución que contiene un proyecto Web de sitio remoto desde el control de código fuente|1. cree un proyecto Web de sitio remoto.<br />2. Agregue la solución al control de código fuente. Si este paso se realiza correctamente, continúe con el paso siguiente.<br />3. Cierre la solución.<br />4. Abra la solución desde el control de código fuente a una nueva ubicación.|`Result from Step 2:`<br /><br /> La web del sitio remoto no está bajo control de código fuente.<br /><br /> `Result from Step 4:`<br /><br /> Solución abierta desde el control de código fuente.<br /><br /> El proyecto de sitio remoto está cargado, pero no está bajo control de código fuente.|

### <a name="case-1c-add-solution-from-source-control"></a>Caso 1c: Adición de la solución desde el control de código fuente
 Este caso de prueba se centra en agregar soluciones desde el control de código fuente.

|Acción|Pasos de prueba|Resultados esperados que se van a comprobar|
|------------|----------------|--------------------------------|
|Agregar a una solución vacía: una solución de un solo proyecto|1. cree una solución de proyecto único.<br />2. Agregue la solución al control de código fuente.<br />3. Cierre la solución.<br />4. cree una segunda solución vacía.<br />5. agregar la solución controlada previamente desde el control de código fuente (**archivo**, **control de código fuente**, **Agregar proyecto desde el control de código fuente**).|El proyecto agregado aparece en **Explorador de soluciones** y está protegido.|
|Agregar a la solución con un solo proyecto: proyecto único|1. cree una solución con un solo proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Cierre la solución.<br />4. cree una segunda solución vacía.<br />5. agregar la solución controlada previamente desde el control de código fuente (**archivo**, **control de código fuente**, **Agregar proyecto desde el control de código fuente**).|El proyecto agregado aparece en **Explorador de soluciones** y está protegido.|
|Agregar a solución: solución agregada al control de código fuente mediante selección|1. cree una solución con un proyecto.<br />2. Agregue solo la solución al control de código fuente como selección. Si este paso se realiza correctamente, continúe con el paso siguiente.<br />3. Cierre la solución.<br />4. cree una nueva solución.<br />5. agregar la solución controlada previamente desde el control de código fuente (**archivo**, **control de código fuente**, **Agregar proyecto desde el control de código fuente**).|`Result from Step 2:`<br /><br /> El proyecto no está bajo control de código fuente.<br /><br /> `Result from Step 5:`<br /><br /> Si la primera solución tenía elementos de la solución, no se pueden agregar desde el control de código fuente, por lo que no aparecen.<br /><br /> El proyecto de la primera solución aparece como no disponible.|

## <a name="see-also"></a>Vea también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
