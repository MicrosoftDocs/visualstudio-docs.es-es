---
title: "Zona de ensayo 4: Comprobar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control de código fuente [Visual Studio SDK], proteger elementos"
  - "origen control complementos, proteger elementos"
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Zona de ensayo 4: Comprobar
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta área de complemento de prueba de control de código fuente cubre enviar elementos actualizados en el almacén de versiones a través de la **proteger** comando.  
  
## Acceso al menú de comandos  
 La siguiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rutas de menú del entorno de desarrollo integrado se utilizan en los casos de prueba.  
  
##### Proteger:  
 **Archivo**, **Control de código fuente**, **proteger**.  
  
 **Archivo**, **proteger**.  
  
 Menú contextual, **proteger**.  
  
## Comportamiento esperado comunes  
  
-   Proyectos y archivos que se agregan a una solución o proyecto bajo control de código fuente aparecen en la **proteger** cuadro de diálogo y el **protecciones pendientes** ventana.  
  
-   Después de la comprobación en, los elementos agregados aparecen en el control de código fuente.  
  
-   Después de la comprobación en, los elementos actualizados están correctamente en el almacén.  
  
## Casos de prueba  
 Los siguientes son los casos de prueba concretos para la zona de ensayo de protección.  
  
### Caso 4: modificar elementos  
 Describe cómo utilizar la comprobación de acción para actualizar un archivo bajo control de código fuente que se ha modificado.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|---------------------|-----------------------------------------|  
|Modificar un archivo de texto que se ha desprotegido, compruebe en el archivo sólo \(**proteger** cuadro de diálogo\)|1.  Cree un nuevo proyecto con un archivo de texto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Desproteger y modificar el archivo de texto.<br />4.  Proteger mediante el cuadro de diálogo Proteger \(**archivo**, **Control de código fuente**, **proteger**\).|Comportamiento esperado común.|  
|Modificar un archivo de texto que se ha desprotegido, compruebe en el archivo sólo \(**protecciones pendientes** ventana\)|1.  Cree un nuevo proyecto con un archivo de texto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Desproteger y modificar el archivo de texto.<br />4.  Proteger a través de la **protecciones pendientes** ventana.|Comportamiento esperado común.|  
  
### Caso 4b: agregar archivos  
 Cuando se agrega un archivo a un proyecto o un elemento a una solución, debe cambiar también el proyecto o solución. Por lo tanto, el archivo primario también está desprotegido y debe estar protegido para completar la adición.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|---------------------|-----------------------------------------|  
|Agregue un archivo de texto y proteger todo \(**proteger** cuadro de diálogo\)|1.  Cree un nuevo proyecto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Agregue un archivo de texto al proyecto.<br />4.  Aceptar la desprotección del proyecto si se le solicita.<br />5.  Seleccione la solución en **el Explorador de soluciones**.<br />6.  Registrar desde el **proteger** cuadro de diálogo.|Comportamiento esperado común.|  
|Agregue un archivo de texto y proteger todo \(**protecciones pendientes** ventana\)|1.  Cree un nuevo proyecto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Agregue un archivo de texto al proyecto.<br />4.  Aceptar la desprotección del proyecto si se le solicita.<br />5.  Proteger la solución de **protecciones pendientes** ventana.|Comportamiento esperado comunes|  
  
### Caso 4c: agregar proyectos  
 Al agregar un proyecto a una solución, debe cambiar también la solución. Por lo tanto, el archivo de solución también está desprotegido y debe protegerse para completar la adición.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|---------------------|-----------------------------------------|  
|Agregar un proyecto a una solución bajo control de código fuente en blanco \(**proteger** cuadro de diálogo\)|1.  Crear una solución en blanco.<br />2.  Agregar la solución al control de código fuente.<br />3.  Agregue un nuevo proyecto.<br />4.  Aceptar la desprotección de la solución si se le solicita.<br />5.  Registrar desde el **proteger** cuadro de diálogo.|Comportamiento esperado común.|  
|Agregar un proyecto a una solución bajo control de código fuente en blanco \(**protecciones pendientes** ventana\)|1.  Crear una solución en blanco.<br />2.  Agregar la solución al control de código fuente.<br />3.  Agregue un nuevo proyecto.<br />4.  Aceptar la desprotección de la solución si se le solicita.<br />5.  Proteger la solución de **protecciones pendientes** ventana.|Comportamiento esperado común.|  
  
## Vea también  
 [Guía de pruebas para los complementos de Control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)