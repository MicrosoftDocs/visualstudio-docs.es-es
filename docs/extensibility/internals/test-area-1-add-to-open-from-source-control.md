---
title: "&#193;rea de prueba 1: Agregar para abrir Control de c&#243;digo fuente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control de código fuente [Visual Studio SDK], agregar y abrir soluciones"
  - "origen control complementos, agregar y abrir soluciones"
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# &#193;rea de prueba 1: Agregar a abrir desde el Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Este complemento de control de origen de prueba área abarca la colocación de soluciones o proyectos bajo control de código fuente y recuperarlos desde el control de código fuente.  
  
## Acceso al menú de comandos  
 La siguiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rutas de menú del entorno de desarrollo integrado se utilizan en los casos de prueba:  
  
-   Para [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], abrir desde el control de código fuente: **archivo**, **Abrir**, **proyecto**\/**solución**; busque en el [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ubicación.  
  
-   Para otros origen control complementos, abra el control de código fuente: **archivo**, **Control de código fuente**, **Abrir desde el Control de código fuente**.  
  
-   Agregar al control de código fuente: **archivo**, **Control de código fuente**, **Agregar solución al archivo de Control de código fuente**, **Control de código fuente**, **Agregar proyectos seleccionados al Control de código fuente**.  
  
-   Menú contextual \(proyecto o solución\), **Agregar solución al Control de código fuente**.  
  
-   Agregar control de código fuente: **archivo**, **Control de código fuente**, **Agregar proyecto desde el Control de código fuente**.  
  
-   Para [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], agregar control de código fuente también está disponible desde **archivo**, **Agregar**, **proyecto existente**; busque en el [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ubicación.  
  
    > [!NOTE]
    >  Una ruta de acceso de un archivo local o un servidor de IIS local \(servidor web\) puede usarse en esta prueba.  
  
## Comportamiento esperado  
  
-   Para cada tipo de proyecto compatibles, un usuario debe ser capaz de "Agregar a" y "Abrir" Control de código fuente.  
  
-   Cuando se agrega un proyecto al Control de código fuente correspondiente \<*ProjectName*\> se crea archivos \(archivo proyecto sugerencia\). Contiene información de conexión y la lista del archivo de exclusión. No elimine este archivo porque contiene información específica para el proyecto.  
  
-   Cuando se agrega una solución al control de código fuente correspondiente \<*SolutionName*\> se crea el archivo entre otros \(triple S\). El archivo de texto contiene la información de conexión y una lista de archivos de exclusión, similar al archivo de sugerencia del proyecto. Este archivo es temporal y sólo existe en la base de datos de control de código fuente.  
  
-   Cuando se abre una solución desde el control de código fuente, un \<*SolutionName*\> archivo .vsscc \(S double\) que sólo existe en la base de datos de control de código fuente, se crea localmente en un archivo temporal. Este archivo contiene la ruta de acceso de la carpeta de conexión de la solución para el archivo de solución. Este archivo es temporal y se elimina la copia local una vez finalizada la operación de "Abrir desde Control de código fuente".  
  
-   Después de agrega un proyecto al control de código fuente, puede realizar las acciones de control de código fuente en él \(desprotección, Get etc.\).  
  
## Casos de prueba  
 Los siguientes son los casos de prueba concretos para agregar \/ abrir desde el área de ensayo de Control de código fuente.  
  
### Caso 1a: Agregar solución al Control de código fuente  
 Este caso de prueba se centra en Agregar soluciones al control de código fuente.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|---------------------|-----------------------------------------|  
|Agregar la solución que contenga un proyecto de cliente para el control de código fuente|1.  Cree un proyecto de cliente.<br />2.  Agregar la solución al control de código fuente \(**archivo**, **Control de código fuente**, **Agregar solución al Control de código fuente**\).|Se agregó la solución o proyecto al control de código fuente.|  
|Agregar la solución que contiene un sistema de archivos o un proyecto Web de IIS local para el control de código fuente|1.  Crear un sistema de archivos o un proyecto Web de IIS local \(utilice el botón Examinar para seleccionar la ubicación del proyecto; la ruta de acceso determina qué tipo de proyecto Web se ha creado\).<br />2.  Agregar la solución al control de código fuente \(**archivo**, **Control de código fuente**, **Agregar solución al Control de código fuente**\).|Se agregó la solución o proyecto al control de código fuente.|  
|Agregar la solución que contiene un proyecto Web de sitio remoto para el control de código fuente|1.  Cree un proyecto Web de sitio remoto.<br />2.  Agregar la solución al control de código fuente \(**archivo**, **Control de código fuente**, **Agregar solución al Control de código fuente**\).<br />3.  Haga clic en **Aceptar** en el cuadro de diálogo de advertencia de acceso de FrontPage.|Se agregó la solución al control de código fuente.<br /><br /> Proyecto de sitio remoto no está bajo control de código fuente. \(Los proyectos de sitio remoto se deben controlar su propio servidor de IIS\).|  
|Agregar una solución de proyecto al control de código fuente mediante **Agregar proyectos seleccionados al Control de código fuente**.|1.  Crear una solución de proyecto único.<br />2.  Agregar sólo solución al control de código fuente como una selección \(**archivo**, **Control de código fuente**, **Agregar proyectos seleccionados al Control de código fuente**\). Si este paso se realiza correctamente, vaya al paso siguiente.<br />3.  Incorporación del proyecto de control de código fuente como selección \(**archivo**, **Control de código fuente**, **Agregar proyectos seleccionados al Control de código fuente**\).<br />4.  Haga clic en **Sí** para agregar el proyecto a la misma ubicación.<br />5.  Haga clic en **Desproteger** en **Desproteger para editar** cuadro de diálogo.|`Result from Step 2:`<br /><br /> El proyecto y todos los archivos del proyecto tienen una espera el indicador de control de código fuente y una información sobre herramientas muestra "no están bajo control de código fuente".<br /><br /> `Result from Step 5:`<br /><br /> Archivo de proyecto y la solución se encuentran en la misma carpeta de control de código fuente.|  
|Cancelar la adición de una solución al control de código fuente|1.  Crear una solución de proyecto único.<br />2.  Intento de agregar proyectos y soluciones al control de código fuente. Si este paso se realiza correctamente, vaya al paso siguiente.<br />3.  Cancelar después de que se encuentra en el sistema de control de código fuente.|`Result from Step 2:`<br /><br /> El cuadro de diálogo de control de origen de conjunto proyecto ubicación aparece una sola vez.<br /><br /> `Result from Step 3:`<br /><br /> Proyecto ha cancelado la agregación, proyecto o solución no está bajo control de código fuente y todos agregan a menús del control de código fuente sigue disponibles.|  
  
### Escenario 1b. Abrir solución desde el Control de código fuente  
 Este caso de prueba se centra en Abrir soluciones desde control de código fuente.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|---------------------|-----------------------------------------|  
|Abra una solución que contenga un proyecto de cliente de control de código fuente|1.  Cree un proyecto de cliente.<br />2.  Agregar la solución al control de código fuente.<br />3.  Cierre la solución.<br />4.  Abra la solución de control de código fuente a una nueva ubicación.|Abrir solución o proyecto de control de código fuente.|  
|Abra una solución que contenga un local o un proyecto Web de IIS desde el control de código fuente|1.  Crear un local o un proyecto Web de IIS.<br />2.  Agregar la solución al control de código fuente.<br />3.  Cierre la solución.<br />4.  Abra la solución de control de código fuente a una nueva ubicación.|Abrir solución o proyecto de control de código fuente.|  
|Abra una solución que contenga un proyecto Web de sitio remoto desde el control de código fuente|1.  Cree un proyecto Web de sitio remoto.<br />2.  Agregar la solución al control de código fuente. Si este paso se realiza correctamente, vaya al paso siguiente.<br />3.  Cierre la solución.<br />4.  Abra la solución de control de código fuente a una nueva ubicación.|`Result from Step 2:`<br /><br /> Web de sitio remoto no está bajo control de código fuente.<br /><br /> `Result from Step 4:`<br /><br /> Abre solución desde el control de código fuente.<br /><br /> Se carga el proyecto de sitio remoto, pero no está bajo control de código fuente.|  
  
### Caso 1c: agregar la solución de Control de código fuente  
 Este caso de prueba se centra en Agregar soluciones de control de código fuente.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|---------------------|-----------------------------------------|  
|Agregar a solución vacía, una solución de proyecto único|1.  Crear una solución de proyecto único.<br />2.  Agregar la solución al control de código fuente.<br />3.  Cierre la solución.<br />4.  Cree una segunda solución vacía.<br />5.  Agregue la solución controlada previamente desde el control de código fuente \(**archivo**, **Control de código fuente**, **Agregar proyecto desde el Control de código fuente**\).|El proyecto agregado aparece en **el Explorador de soluciones** y está protegido.|  
|Agregar a solución con el único proyecto: un proyecto único|1.  Crear una solución con un solo proyecto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Cierre la solución.<br />4.  Cree una segunda solución vacía.<br />5.  Agregue la solución controlada previamente desde el control de código fuente \(**archivo**, **Control de código fuente**, **Agregar proyecto desde el Control de código fuente**\).|El proyecto agregado aparece en **el Explorador de soluciones** y está protegido.|  
|Agregar a solución: solución agregado al control de código fuente por selección|1.  Crear una solución con un proyecto.<br />2.  Agregar sólo solución al control de código fuente como selección. Si este paso se realiza correctamente, vaya al paso siguiente.<br />3.  Cierre la solución.<br />4.  Crear una nueva solución.<br />5.  Agregue la solución controlada previamente desde el control de código fuente \(**archivo**, **Control de código fuente**, **Agregar proyecto desde el Control de código fuente**\).|`Result from Step 2:`<br /><br /> Proyecto no está bajo control de código fuente.<br /><br /> `Result from Step 5:`<br /><br /> Si la primera solución tenía elementos de solución, no se puede agregar desde el control de código fuente, por lo que no aparecen.<br /><br /> Proyecto de la primera solución aparece como no disponible.|  
  
## Vea también  
 [Guía de pruebas para los complementos de Control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)