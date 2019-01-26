---
title: 'Área de prueba 4: Compruebe | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81b96a97faef5bc86b0d8c6321674310e86ad1fd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936611"
---
# <a name="test-area-4-check-in"></a>Área de prueba 4: Proteger
Esta área de prueba de complemento de control de código fuente trata de enviar los elementos actualizados en el almacén de versiones a través de la **proteger** comando.  
  
## <a name="command-menu-access"></a>Acceso al menú de comandos  
 La siguiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rutas de menú del entorno de desarrollo integrado que se usan en los casos de prueba.  
  
##### <a name="check-in"></a>Check-in:  
 **Archivo**, **Control de código fuente**, **proteger**.  
  
 **Archivo**, **proteger**.  
  
 Menú contextual, **proteger**.  
  
## <a name="common-expected-behavior"></a>Comportamiento esperado comunes  
  
-   Proyectos y archivos agregados a una solución o proyecto bajo control de código fuente aparecen en la **proteger** cuadro de diálogo y el **protecciones pendientes** ventana.  
  
-   Después de la comprobación en, los elementos agregados aparecen en el control de código fuente.  
  
-   Después de la comprobación en, los elementos actualizados son versiones correctas en el almacén.  
  
## <a name="test-cases"></a>Casos de prueba  
 Los siguientes son casos de prueba concretos para el área de prueba de inserción en el repositorio.  
  
### <a name="case-4a-modified-items"></a>Escenario 4a: Elementos modificados  
 Describe cómo usar la verificación en acción para actualizar un archivo bajo control de código fuente que se ha modificado.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Modificar un archivo de texto que se ha desprotegido, compruebe en el archivo solo (**proteger** cuadro de diálogo)|1.  Cree un nuevo proyecto con un archivo de texto.<br />2.  Agregue la solución al control de código fuente.<br />3.  Desproteger y modificar el archivo de texto.<br />4.  Proteger a través del cuadro de diálogo Insertar en el repositorio (**archivo**, **Control de código fuente**, **proteger**).|Comportamiento esperado común.|  
|Modificar un archivo de texto que se ha desprotegido, compruebe en el archivo solo (**protecciones pendientes** ventana)|1.  Cree un nuevo proyecto con un archivo de texto.<br />2.  Agregue la solución al control de código fuente.<br />3.  Desproteger y modificar el archivo de texto.<br />4.  Proteger a través de la **protecciones pendientes** ventana.|Comportamiento esperado común.|  
  
### <a name="case-4b-adding-files"></a>Escenario 4b: Agregar archivos  
 Al agregar un archivo a un proyecto o un elemento a una solución, debe cambiar también el proyecto o solución. Por lo tanto, el archivo primario también está desprotegido y debe protegerse para completar la incorporación.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Agregar un archivo de texto y proteger todo (**proteger** cuadro de diálogo)|1.  Cree un nuevo proyecto.<br />2.  Agregue la solución al control de código fuente.<br />3.  Agregue un archivo de texto al proyecto.<br />4.  Si se le solicite, acepte desprotección del proyecto.<br />5.  Seleccione la solución en **el Explorador de soluciones**.<br />6.  Proteger desde el **proteger** cuadro de diálogo.|Comportamiento esperado común.|  
|Agregar un archivo de texto y proteger todo (**protecciones pendientes** ventana)|1.  Cree un nuevo proyecto.<br />2.  Agregue la solución al control de código fuente.<br />3.  Agregue un archivo de texto al proyecto.<br />4.  Si se le solicite, acepte desprotección del proyecto.<br />5.  Proteja la solución de **protecciones pendientes** ventana.|Comportamiento esperado comunes|  
  
### <a name="case-4c-adding-projects"></a>Caso 4 núcleos: Agregar proyectos  
 Al agregar un proyecto a una solución, debe cambiar también la solución. Por lo tanto, el archivo de solución también está desprotegido y debe protegerse para completar la incorporación.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Agregar un proyecto a una solución bajo control de código fuente en blanco (**proteger** cuadro de diálogo)|1.  Crear una solución en blanco.<br />2.  Agregue la solución al control de código fuente.<br />3.  Agregue un proyecto nuevo.<br />4.  Si se le solicite, acepte desprotección de la solución.<br />5.  Proteger desde el **proteger** cuadro de diálogo.|Comportamiento esperado común.|  
|Agregar un proyecto a una solución bajo control de código fuente en blanco (**protecciones pendientes** ventana)|1.  Crear una solución en blanco.<br />2.  Agregue la solución al control de código fuente.<br />3.  Agregue un proyecto nuevo.<br />4.  Si se le solicite, acepte desprotección de la solución.<br />5.  Proteja la solución de **protecciones pendientes** ventana.|Comportamiento esperado común.|  
  
## <a name="see-also"></a>Vea también  
 [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)