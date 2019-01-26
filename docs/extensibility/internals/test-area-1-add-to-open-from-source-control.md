---
title: 'Área de prueba 1: Agregar a / abrir desde Control de código fuente | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd60d4c042e7fa27386ef549ce6b9d8e808a3176
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962880"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Área de prueba 1: Agregar a / abrir desde Control de código fuente
Este complemento de control de origen de prueba área abarca la colocación de las soluciones o proyectos bajo control de código fuente y recuperarlos desde el control de código fuente.  
  
## <a name="command-menu-access"></a>Acceso al menú de comandos  
 La siguiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rutas de menú del entorno de desarrollo integrado que se usan en los casos de prueba:  
  
- Para [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], abrir desde el control de código fuente: **Archivo**, **abierto**, **proyecto**/**solución**; busque en el [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ubicación.  
  
- Para otros complementos código fuente control, abra el control de código fuente: **Archivo**, **Control de código fuente**, **abrir desde el Control de código fuente**.  
  
- Agregar a control de código fuente: **Archivo**, **Control de código fuente**, **Agregar solución al archivo de Control de código fuente**, **Control de código fuente**, **agregar proyectos seleccionados al Control de código fuente**.  
  
- Menú contextual (proyecto o solución), **Agregar solución al Control de código fuente**.  
  
- Agregar desde el control de código fuente: **Archivo**, **Control de código fuente**, **Agregar proyecto desde el Control de código fuente**.  
  
- Para [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], agregar control de código fuente también está disponible en **archivo**, **agregar**, **proyecto existente**; Fíjese en el [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ubicación.  
  
  > [!NOTE]
  >  En esta prueba se puede usar una ruta de acceso de un archivo local o un servidor de IIS local (servidor web).  
  
## <a name="expected-behavior"></a>Comportamiento esperado  
  
-   Para cada tipo de proyecto compatible, un usuario debe ser capaz de "Agregar a" y "Abrir desde" Control de código fuente.  
  
-   Cuando se agrega un proyecto de control de código fuente, correspondiente \< *ProjectName*> se crea el archivo .SCC (archivo de indicaciones de proyecto). Contiene información de conexión y lista de archivos de exclusión. No elimine este archivo porque contiene información específica del proyecto.  
  
-   Cuando se agrega una solución al control de código fuente correspondiente \< *SolutionName*> se crea el archivo entre otros (triple S). El archivo de texto contiene la información de conexión y una lista de archivos de exclusión, similar al archivo de sugerencia del proyecto. Este archivo es temporal y sólo existe en la base de datos de control de código fuente.  
  
-   Cuando se abre una solución de control de código fuente, un \< *SolutionName*> archivo .vsscc (doble S) que solo existe en la base de datos de control de código fuente, se crea localmente en un archivo temporal. Este archivo contiene la ruta de acceso de la carpeta de conexión de la solución para el archivo de solución. Este archivo es temporal y se elimina la copia local cuando se ha completado la operación de "Abrir desde Control de código fuente".  
  
-   Después de agrega un proyecto al control de origen, puede realizar las acciones de control de código fuente en ella (consulte, Get y así sucesivamente).  
  
## <a name="test-cases"></a>Casos de prueba  
 Los siguientes son casos de prueba concretos para agregar a / abrir desde el área de prueba de Control de código fuente.  
  
### <a name="case-1a-add-solution-to-source-control"></a>Case 1a: Agregar solución al Control de código fuente  
 En este caso de prueba se centra en Agregar soluciones al control de código fuente.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Agregar la solución que contiene un proyecto de cliente para el control de código fuente|1.  Cree un proyecto de cliente.<br />2.  Agregue la solución al control de código fuente (**archivo**, **Control de código fuente**, **Agregar solución al Control de código fuente**).|Se agregó la solución o proyecto al control de código fuente.|  
|Agregar la solución que contiene un sistema de archivos o un proyecto Web de IIS local para el control de código fuente|1.  Crear un proyecto Web de IIS local o un sistema de archivos (use el botón Examinar para seleccionar la ubicación del proyecto; la ruta de acceso determina qué tipo de proyecto Web se crea).<br />2.  Agregue la solución al control de código fuente (**archivo**, **Control de código fuente**, **Agregar solución al Control de código fuente**).|Se agregó la solución o proyecto al control de código fuente.|  
|Agregar la solución que contiene un proyecto Web de sitio remoto para el control de código fuente|1.  Cree un proyecto Web de sitio remoto.<br />2.  Agregue la solución al control de código fuente (**archivo**, **Control de código fuente**, **Agregar solución al Control de código fuente**).<br />3.  Haga clic en **Aceptar** en el cuadro de diálogo de advertencia de acceso de FrontPage.|Se agregó la solución al control de código fuente.<br /><br /> Proyecto de sitio remoto no está bajo control de código fuente. (Los proyectos de sitio remoto deben controlarse desde su propio servidor IIS).|  
|Agregar una solución de proyecto único al control de código fuente mediante **agregar proyectos seleccionados al Control de código fuente**.|1.  Crear una solución de proyecto único.<br />2.  Agregue solo solución al control de código fuente como una selección (**archivo**, **Control de código fuente**, **agregar proyectos seleccionados al Control de código fuente**). Si este paso se realiza correctamente, vaya al paso siguiente.<br />3.  Agregar proyecto al control de código fuente como selección (**archivo**, **Control de código fuente**, **agregar proyectos seleccionados al Control de código fuente**).<br />4.  Haga clic en **Sí** para agregar el proyecto en la misma ubicación.<br />5.  Haga clic en **desproteger** en **desproteger para editar** cuadro de diálogo.|`Result from Step 2:`<br /><br /> El proyecto y todos los archivos dentro del proyecto tienen un checked out indicador de control de código fuente y una información sobre herramientas muestra "no están bajo control de código fuente".<br /><br /> `Result from Step 5:`<br /><br /> Archivo de solución y proyecto se encuentran en la misma carpeta de control de código fuente.|  
|Cancelar la adición de una solución al control de código fuente|1.  Crear una solución de proyecto único.<br />2.  Intentar agregar soluciones y proyectos al control de código fuente. Si este paso se realiza correctamente, vaya al paso siguiente.<br />3.  Cancelar una vez que se encuentra en el sistema de control de código fuente.|`Result from Step 2:`<br /><br /> El cuadro de diálogo de control de origen de conjunto proyecto ubicación aparece una sola vez.<br /><br /> `Result from Step 3:`<br /><br /> Proyecto ha cancelado la agregación, proyecto o solución no está bajo control de código fuente y agregan todas a los menús del control de código fuente sigue disponibles.|  
  
### <a name="case-1b-open-solution-from-source-control"></a>Escenario 1b. Abrir solución desde el Control de código fuente  
 En este caso de prueba se centra en Abrir soluciones desde control de código fuente.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Abra una solución que contenga un proyecto de cliente de control de código fuente|1.  Cree un proyecto de cliente.<br />2.  Agregue la solución al control de código fuente.<br />3.  Cierre la solución.<br />4.  Abra la solución del control de código fuente a una nueva ubicación.|Abrir solución o proyecto de control de código fuente.|  
|Abra una solución que contenga un local o un proyecto Web de IIS desde control de código fuente|1.  Cree una local o un proyecto Web de IIS.<br />2.  Agregue la solución al control de código fuente.<br />3.  Cierre la solución.<br />4.  Abra la solución del control de código fuente a una nueva ubicación.|Abrir solución o proyecto de control de código fuente.|  
|Abrir una solución que contiene un proyecto Web de sitio remoto desde el control de código fuente|1.  Cree un proyecto Web de sitio remoto.<br />2.  Agregue la solución al control de código fuente. Si este paso se realiza correctamente, vaya al paso siguiente.<br />3.  Cierre la solución.<br />4.  Abra la solución del control de código fuente a una nueva ubicación.|`Result from Step 2:`<br /><br /> Web de sitio remoto no está bajo control de código fuente.<br /><br /> `Result from Step 4:`<br /><br /> Abre solución desde control de código fuente.<br /><br /> Se carga el proyecto de sitio remoto, pero no está bajo control de código fuente.|  
  
### <a name="case-1c-add-solution-from-source-control"></a>Caso 1C: Agregar solución desde Control de código fuente  
 En este caso de prueba se centra en Agregar soluciones desde control de código fuente.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Agregar a solución vacía, una solución de proyecto único|1.  Crear una solución de proyecto único.<br />2.  Agregue la solución al control de código fuente.<br />3.  Cierre la solución.<br />4.  Cree una segunda solución vacía.<br />5.  Agregar la solución controlada previamente desde control de código fuente (**archivo**, **Control de código fuente**, **Agregar proyecto desde el Control de código fuente**).|El proyecto agregado aparece en **el Explorador de soluciones** y está protegido.|  
|Agregar a solución con un proyecto único, un proyecto único|1.  Crear una solución con un solo proyecto.<br />2.  Agregue la solución al control de código fuente.<br />3.  Cierre la solución.<br />4.  Cree una segunda solución vacía.<br />5.  Agregar la solución controlada previamente desde control de código fuente (**archivo**, **Control de código fuente**, **Agregar proyecto desde el Control de código fuente**).|El proyecto agregado aparece en **el Explorador de soluciones** y está protegido.|  
|Agregar a solución, agregado control de código fuente mediante la selección de soluciones|1.  Crear una solución con un proyecto.<br />2.  Agregar solo solución al control de código fuente como selección. Si este paso se realiza correctamente, vaya al paso siguiente.<br />3.  Cierre la solución.<br />4.  Crear una nueva solución.<br />5.  Agregar la solución controlada previamente desde control de código fuente (**archivo**, **Control de código fuente**, **Agregar proyecto desde el Control de código fuente**).|`Result from Step 2:`<br /><br /> Proyecto no está bajo control de código fuente.<br /><br /> `Result from Step 5:`<br /><br /> Si la primera solución tenía elementos de la solución, no se puede agregar desde el control de código fuente, por lo que no aparecen.<br /><br /> Proyecto de la primera solución aparecerá como no disponible.|  
  
## <a name="see-also"></a>Vea también  
 [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)