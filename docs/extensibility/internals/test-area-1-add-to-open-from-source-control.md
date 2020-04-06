---
title: 'Zona de prueba 1: Añadir a abierto desde el control de código fuente Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ac7b8e5a60fe25ac22272cc28fc3ed6f903b058
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704679"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Zona de prueba 1: Añadir a/Abrir desde el Control de código fuente
Este área de prueba del complemento de control de código fuente cubre la colocación de soluciones o proyectos bajo control de código fuente y la recuperación de ellos del control de código fuente.

## <a name="command-menu-access"></a>Acceso al menú de comandos
 En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] los casos de prueba se utilizan las siguientes rutas de menú del entorno de desarrollo integrado:

- Para [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], abrir desde el control de código fuente: **Archivo**, **Abrir**,**Solución** **de proyecto**/; mirar en [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] la ubicación.

- Para otros complementos de control de código fuente, abierto desde el control de código fuente: **Archivo**, **Control de código fuente**, Abrir desde Control de código **fuente**.

- Agregar al control de código fuente: **Archivo**, **Control de código fuente**, Agregar **solución al archivo**de control de código fuente , Control de código **fuente**, Agregar **proyectos seleccionados al Control de código fuente**.

- Menú contextual (proyecto/solución), **Agregar solución al control de código fuente**.

- Agregar desde el control de código fuente: **Archivo**, **Control de código fuente**, Agregar proyecto desde Control de código **fuente**.

- Para [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], add from source control también está disponible desde **Archivo**, **Agregar**, **Proyecto existente**; mirar en [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] la ubicación.

  > [!NOTE]
  > En esta prueba se puede utilizar una ruta de acceso de un archivo local o un IIS local (servidor web).

## <a name="expected-behavior"></a>Comportamiento esperado

- Para cada tipo de proyecto admitido, un usuario debe poder "Agregar a" y "Abrir desde" Control de código fuente.

- Cuando se agrega un proyecto al \<Control de código fuente, se crea un archivo *ProjectName*>.vspscc correspondiente (archivo de sugerencia de proyecto). Contiene la lista de archivos de exclusión y la información de conexión. No elimine este archivo porque contiene información específica del proyecto.

- Cuando se agrega una solución \<al control de código fuente, se crea un archivo *SolutionName*>.vssscc (triple S) correspondiente. El archivo de texto contiene información de conexión y una lista de archivos de exclusión, similar al archivo de sugerencia del proyecto. Este archivo es temporal y solo existe en la base de datos de control de código fuente.

- Cuando se abre una solución \<desde el control de código fuente, un *SolutionName*>.vsscc (doble S) archivo que existe solo en la base de datos de control de código fuente, se crea localmente en un archivo temporal. Este archivo contiene la ruta de acceso de la carpeta de conexión de la solución al archivo de solución. Este archivo es temporal y la copia local se elimina cuando se ha completado la operación "Abrir desde control de código fuente".

- Después de agregar un proyecto al control de código fuente, puede realizar cualquier acción de control de código fuente en él (Desproteger, Obtener, etc.).

## <a name="test-cases"></a>Casos de prueba
 A continuación se muestran casos de prueba específicos para el área de prueba Agregar a/Abrir desde el control de código fuente.

### <a name="case-1a-add-solution-to-source-control"></a>Caso 1a: Agregar solución al control de código fuente
 Este caso de prueba se centra en agregar soluciones al control de código fuente.

|Acción|Pasos de prueba|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Agregar solución que contenga un proyecto de cliente al control de código fuente|1. Cree un proyecto de cliente.<br />2. Agregue la solución al control de código fuente (**File**, **Source Control**, Add Solution to **Source Control**).|Solución/Proyecto se agregó al control de código fuente.|
|Agregar solución que contenga un sistema de archivos o un proyecto web IIS local al control de código fuente|1. Cree un sistema de archivos o un proyecto web IIS local (utilice el botón Examinar para apuntar a la ubicación del proyecto; la ruta de acceso determina qué tipo de proyecto Web se crea).<br />2. Agregue la solución al control de código fuente (**File**, **Source Control**, Add Solution to **Source Control**).|Solución/Proyecto se agregó al control de código fuente.|
|Agregar solución que contenga un proyecto Web de sitio remoto al control de código fuente|1. Cree un proyecto Web de sitio remoto.<br />2. Agregue la solución al control de código fuente (**File**, **Source Control**, Add Solution to **Source Control**).<br />3. Hacer clic **OK** en FrontPage Access cuadro de diálogo de advertencia.|Solución se agregó al control de código fuente.<br /><br /> Proyecto de sitio remoto NO está bajo control de código fuente. (Los proyectos de sitio remoto deben controlarse desde su propio servidor IIS.)|
|Agregue una única solución de proyecto al control de código fuente mediante **Agregar proyectos seleccionados al control de código fuente**.|1. Cree una única solución de proyecto.<br />2. Agregue solo solución al control de código fuente como una selección (**Archivo**, **Control de código fuente**, Agregar proyectos **seleccionados al Control de código fuente**). Si este paso se realiza correctamente, continúe con el paso siguiente.<br />3. Agregue el proyecto al control de código fuente como selección (**Archivo**, **Control de código fuente**, Agregar proyectos **seleccionados al Control de código fuente**).<br />4. Haga clic en **Sí** para agregar el proyecto a la misma ubicación.<br />5. Hacer clic **Desproteger** en **Desproteger para editar** cuadro de diálogo.|`Result from Step 2:`<br /><br /> El proyecto y todos los archivos del proyecto tienen un indicador de control de código fuente desprotegido y una información sobre herramientas muestra "No bajo control de código fuente".<br /><br /> `Result from Step 5:`<br /><br /> El proyecto y el archivo de solución están en la misma carpeta en el control de código fuente.|
|Cancelar la adición de una solución al control de código fuente|1. Cree una única solución de proyecto.<br />2. Intente agregar proyecto y solución al control de código fuente. Si este paso se realiza correctamente, continúe con el paso siguiente.<br />3. Cancelar después de que usted está en el sistema de control de código fuente.|`Result from Step 2:`<br /><br /> El cuadro de diálogo Establecer control de código fuente de ubicación del proyecto solo aparece una vez.<br /><br /> `Result from Step 3:`<br /><br /> Agregar proyecto cancelado, proyecto/solución NO está bajo control de código fuente y todos los menús Agregar al control de código fuente todavía están disponibles.|

### <a name="case-1b-open-solution-from-source-control"></a>Caso 1b. Solución abierta desde el Control de código fuente
 Este caso de prueba se centra en la apertura de soluciones desde el control de código fuente.

|Acción|Pasos de prueba|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Abra una solución que contenga un proyecto de cliente desde el control de código fuente|1. Cree un proyecto de cliente.<br />2. Agregue la solución al control de código fuente.<br />3. Cierre la solución.<br />4. Abra la solución desde el control de código fuente a una nueva ubicación.|Solución/Proyecto abierto desde el control de código fuente.|
|Abra una solución que contenga un proyecto web local o IIS desde el control de código fuente|1. Cree un proyecto web local o IIS.<br />2. Agregue la solución al control de código fuente.<br />3. Cierre la solución.<br />4. Abra la solución desde el control de código fuente a una nueva ubicación.|Solución/Proyecto abierto desde el control de código fuente.|
|Abra una solución que contenga un proyecto Web de sitio remoto desde el control de código fuente|1. Cree un proyecto Web de sitio remoto.<br />2. Agregue la solución al control de código fuente. Si este paso se realiza correctamente, continúe con el paso siguiente.<br />3. Cierre la solución.<br />4. Abra la solución desde el control de código fuente a una nueva ubicación.|`Result from Step 2:`<br /><br /> Web del sitio remoto NO está bajo control de código fuente.<br /><br /> `Result from Step 4:`<br /><br /> Solución abierta desde el control de código fuente.<br /><br /> Se carga el proyecto de sitio remoto, pero NO está bajo control de código fuente.|

### <a name="case-1c-add-solution-from-source-control"></a>Caso 1c: Agregar solución desde el Control de código fuente
 Este caso de prueba se centra en agregar soluciones desde el control de código fuente.

|Acción|Pasos de prueba|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Añadir a la solución vacía: una solución de proyecto único|1. Cree una única solución de proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Cierre la solución.<br />4. Cree una segunda solución vacía.<br />5. Agregue la solución previamente controlada desde el control de código fuente (**File**, **Source Control**, Add Project from **Source Control**).|El proyecto agregado aparece en el Explorador de **soluciones** y está protegido.|
|Añadir a la solución con un solo proyecto — proyecto único|1. Cree una solución con un solo proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Cierre la solución.<br />4. Cree una segunda solución vacía.<br />5. Agregue la solución previamente controlada desde el control de código fuente (**File**, **Source Control**, Add Project from **Source Control**).|El proyecto agregado aparece en el Explorador de **soluciones** y está protegido.|
|Añadir a la solución: solución añadida al control de código fuente por selección|1. Cree una solución con un proyecto.<br />2. Agregue solo solución al control de código fuente como selección. Si este paso se realiza correctamente, continúe con el paso siguiente.<br />3. Cierre la solución.<br />4. Cree una nueva solución.<br />5. Agregue la solución previamente controlada desde el control de código fuente (**File**, **Source Control**, Add Project from **Source Control**).|`Result from Step 2:`<br /><br /> Project no está bajo control de código fuente.<br /><br /> `Result from Step 5:`<br /><br /> Si la primera solución tenía elementos de solución, no se pueden agregar desde el control de código fuente, por lo que no aparecen.<br /><br /> El proyecto de la primera solución aparece como no disponible.|

## <a name="see-also"></a>Vea también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
