---
title: "Área de prueba 1: Agregar para abrir desde el Control de código fuente | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 959387176e079d76263a2a5c499b5a0723fd7ad7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Área de prueba 1: Agregar a / Open de Control de código fuente
Este control de código fuente de complemento de prueba área cubre colocando soluciones o proyectos bajo el control de código fuente y recuperarlos desde el control de código fuente.  
  
## <a name="command-menu-access"></a>Acceso al menú de comandos  
 El siguiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] las rutas de acceso del menú de entorno de desarrollo integrado se utilizan en los casos de prueba:  
  
-   Para [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], abrir desde el control de código fuente: **archivo**, **abrir**, **proyecto**/**solución**; busque en el [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ubicación.  
  
-   Para otros origen control complementos, abra el control de código fuente: **archivo**, **Control de código fuente**, **abrir desde el Control de código fuente**.  
  
-   Agregar al control de código fuente: **archivo**, **Control de código fuente**, **Agregar solución al archivo de Control de código fuente**, **Control de código fuente**, **agregar Proyectos al Control de código fuente seleccionados**.  
  
-   Menú contextual (proyecto/solución), **Agregar solución al Control de código fuente**.  
  
-   Complemento de control de código fuente: **archivo**, **Control de código fuente**, **Agregar proyecto desde el Control de código fuente**.  
  
-   Para [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], agregar control de código fuente también está disponible en **archivo**, **agregar**, **proyecto existente**; busque en el [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ubicación.  
  
    > [!NOTE]
    >  Una ruta de acceso de un archivo local o un servidor de IIS local (servidor web) puede usarse en esta prueba.  
  
## <a name="expected-behavior"></a>Comportamiento esperado  
  
-   Para cada tipo de proyecto compatible, un usuario debe ser capaz de "Agregar a" y "Abrir desde" Control de código fuente.  
  
-   Cuando se agrega un proyecto al Control de código fuente, su correspondiente \< *ProjectName*> se crea el archivo de archivos (archivo de indicaciones de proyecto). Contiene información de conexión y la lista de archivos de exclusión. No elimine este archivo porque contiene información específica del proyecto.  
  
-   Cuando se agrega una solución al control de código fuente, su correspondiente \< *SolutionName*> se crea el archivo entre otros (triple S). El archivo de texto contiene la información de conexión y una lista de archivos de exclusión, similar al archivo de sugerencia del proyecto. Este archivo es temporal y solo existe en la base de datos de control de código fuente.  
  
-   Cuando se abre una solución de control de código fuente, un \< *SolutionName*> archivo .vsscc (S dobles) que solo existe en la base de datos de control de código fuente, se crea localmente en un archivo temporal. Este archivo contiene la ruta de acceso de la carpeta de conexión de la solución para el archivo de solución. Este archivo es temporal y se elimina la copia local cuando se complete la operación de "Abrir desde Control de código fuente".  
  
-   Después de agrega un proyecto para el control de código fuente, puede realizar las acciones de control de origen en él (desprotección, Get y así sucesivamente).  
  
## <a name="test-cases"></a>Casos de prueba  
 Los siguientes son los casos de prueba concretos para el complemento a / Open desde el área de ensayo de Control de código fuente.  
  
### <a name="case-1a-add-solution-to-source-control"></a>Caso 1a: Agregar solución al Control de código fuente  
 Este caso de prueba se centra en Agregar soluciones al control de código fuente.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Agregar la solución que contenga un proyecto de cliente para el control de código fuente|1.  Cree un proyecto de cliente.<br />2.  Agregar la solución al control de código fuente (**archivo**, **Control de código fuente**, **Agregar solución al Control de código fuente**).|Solución o proyecto se agregó al control de código fuente.|  
|Agregar la solución que contenga un sistema de archivos o un proyecto Web de IIS local para el control de código fuente|1.  Crear un sistema de archivos o un proyecto Web de IIS local (utilice el botón Examinar para seleccionar la ubicación del proyecto; la ruta de acceso determina qué tipo de proyecto Web se crea).<br />2.  Agregar la solución al control de código fuente (**archivo**, **Control de código fuente**, **Agregar solución al Control de código fuente**).|Solución o proyecto se agregó al control de código fuente.|  
|Agregar la solución que contenga un proyecto Web de sitio remoto para el control de código fuente|1.  Cree un proyecto Web de sitio remoto.<br />2.  Agregar la solución al control de código fuente (**archivo**, **Control de código fuente**, **Agregar solución al Control de código fuente**).<br />3.  Haga clic en **Aceptar** en el cuadro de diálogo de advertencia de acceso de FrontPage.|Solución se agrega al control de código fuente.<br /><br /> Proyecto de sitio remoto no está bajo control de código fuente. (Proyectos de sitio remoto deben controlarse desde su propio servidor IIS.)|  
|Agregar una solución de proyecto único al control de código fuente mediante **agregar proyectos seleccionados al Control de código fuente**.|1.  Crear una solución de proyecto único.<br />2.  Agregar solo solución al control de código fuente como una selección (**archivo**, **Control de código fuente**, **agregar proyectos seleccionados al Control de código fuente**). Si este paso se realiza correctamente, vaya al paso siguiente.<br />3.  Agregar proyectos al control de código fuente como selección (**archivo**, **Control de código fuente**, **agregar proyectos seleccionados al Control de código fuente**).<br />4.  Haga clic en **Sí** para agregar el proyecto en la misma ubicación.<br />5.  Haga clic en **desproteger** en **desproteger para editar** cuadro de diálogo.|`Result from Step 2:`<br /><br /> El proyecto y todos los archivos en el proyecto tienen un checked out indicador de control de código fuente y una información sobre herramientas muestra "no están bajo control de código fuente".<br /><br /> `Result from Step 5:`<br /><br /> Archivo de proyecto y la solución se encuentran en la misma carpeta de control de código fuente.|  
|Cancelar la adición de una solución al control de código fuente|1.  Crear una solución de proyecto único.<br />2.  Ha intentado agregar proyectos y soluciones al control de código fuente. Si este paso se realiza correctamente, vaya al paso siguiente.<br />3.  Cancelar una vez que se encuentra en el sistema de control de código fuente.|`Result from Step 2:`<br /><br /> El cuadro de diálogo de control de origen de conjunto proyecto ubicación aparece una sola vez.<br /><br /> `Result from Step 3:`<br /><br /> Proyecto ha cancelado la agregación, proyecto o solución no está bajo control de código fuente y todos los agregan a los menús de control de código fuente seguirá estando disponibles.|  
  
### <a name="case-1b-open-solution-from-source-control"></a>Escenario 1b. Abrir solución desde el Control de código fuente  
 Este caso de prueba se centra en Abrir soluciones desde control de código fuente.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Abra una solución que contenga un proyecto de cliente de control de código fuente|1.  Cree un proyecto de cliente.<br />2.  Agregar la solución al control de código fuente.<br />3.  Cierre la solución.<br />4.  Abra la solución de control de código fuente a una nueva ubicación.|Abrir solución o proyecto de control de código fuente.|  
|Abra una solución que contenga un local o un proyecto Web de IIS de control de código fuente|1.  Crear un local o un proyecto Web de IIS.<br />2.  Agregar la solución al control de código fuente.<br />3.  Cierre la solución.<br />4.  Abra la solución de control de código fuente a una nueva ubicación.|Abrir solución o proyecto de control de código fuente.|  
|Abra una solución que contenga un proyecto Web de sitio remoto de control de código fuente|1.  Cree un proyecto Web de sitio remoto.<br />2.  Agregar la solución al control de código fuente. Si este paso se realiza correctamente, vaya al paso siguiente.<br />3.  Cierre la solución.<br />4.  Abra la solución de control de código fuente a una nueva ubicación.|`Result from Step 2:`<br /><br /> Web de sitio remoto no está bajo control de código fuente.<br /><br /> `Result from Step 4:`<br /><br /> Abre solución desde el control de código fuente.<br /><br /> Se carga el proyecto de sitio remoto, pero no está bajo control de código fuente.|  
  
### <a name="case-1c-add-solution-from-source-control"></a>Caso c de 1: agregar la solución de Control de código fuente  
 Este caso de prueba se centra en la adición de soluciones de control de código fuente.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Agregar a solución vacía, una solución de proyecto único|1.  Crear una solución de proyecto único.<br />2.  Agregar la solución al control de código fuente.<br />3.  Cierre la solución.<br />4.  Cree una segunda solución vacía.<br />5.  Agregar la solución controlada previamente del control de código fuente (**archivo**, **Control de código fuente**, **Agregar proyecto desde el Control de código fuente**).|El proyecto agregado aparece en **el Explorador de soluciones** y está activada en.|  
|Agregar a solución con un proyecto único, solo proyecto|1.  Crear una solución con un solo proyecto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Cierre la solución.<br />4.  Cree una segunda solución vacía.<br />5.  Agregar la solución controlada previamente del control de código fuente (**archivo**, **Control de código fuente**, **Agregar proyecto desde el Control de código fuente**).|El proyecto agregado aparece en **el Explorador de soluciones** y está activada en.|  
|Agregar a solución: solución agregado al control de código fuente selección|1.  Crear una solución con un proyecto.<br />2.  Agregar solo solución al control de código fuente como selección. Si este paso se realiza correctamente, vaya al paso siguiente.<br />3.  Cierre la solución.<br />4.  Cree una nueva solución.<br />5.  Agregar la solución controlada previamente del control de código fuente (**archivo**, **Control de código fuente**, **Agregar proyecto desde el Control de código fuente**).|`Result from Step 2:`<br /><br /> Proyecto no está bajo control de código fuente.<br /><br /> `Result from Step 5:`<br /><br /> Si la primera solución tenía elementos de la solución, no se puede agregar desde el control de código fuente, por lo que no aparecen.<br /><br /> Proyecto de la primera solución aparece como no disponible.|  
  
## <a name="see-also"></a>Vea también  
 [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)