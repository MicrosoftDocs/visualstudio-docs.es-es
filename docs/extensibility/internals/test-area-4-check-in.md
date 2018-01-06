---
title: 'Zona de ensayo 4: Comprobar | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 698b46c7ccb0a3fb13c799349d36de0cadf80af1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="test-area-4-check-in"></a>Zona de ensayo 4: Insertar en el repositorio
Esta área de complemento de prueba de control de código fuente trata enviar elementos actualizados en el almacén de versiones a través de la **proteger** comando.  
  
## <a name="command-menu-access"></a>Acceso al menú de comandos  
 El siguiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] las rutas de acceso del menú de entorno de desarrollo integrado se utilizan en los casos de prueba.  
  
##### <a name="check-in"></a>Check-in:  
 **Archivo**, **Control de código fuente**, **proteger**.  
  
 **Archivo**, **proteger**.  
  
 Menú contextual, **proteger**.  
  
## <a name="common-expected-behavior"></a>Comportamiento esperado común  
  
-   Proyectos y archivos que se agreguen a una solución o proyecto bajo control de código fuente aparecen en la **proteger** cuadro de diálogo y el **protecciones pendientes** ventana.  
  
-   Después de la comprobación en, los elementos agregados aparecen en control de código fuente.  
  
-   Después de la comprobación en, los elementos actualizados están correctamente con control de versiones en el almacén.  
  
## <a name="test-cases"></a>Casos de prueba  
 Éstos son los casos de prueba concretos para la zona de ensayo de protección.  
  
### <a name="case-4a-modified-items"></a>Caso 4a: modificar elementos  
 Describe el uso de la comprobación de acción para actualizar un archivo bajo control de código fuente que se ha modificado.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Modificar un archivo de texto que se ha extraído, compruebe en el archivo solo (**proteger** cuadro de diálogo)|1.  Cree un nuevo proyecto con un archivo de texto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Desproteger y modificar el archivo de texto.<br />4.  Insertar en el repositorio mediante el cuadro de diálogo Insertar en el repositorio (**archivo**, **Control de código fuente**, **proteger**).|Comportamiento esperado común.|  
|Modificar un archivo de texto que se ha extraído, compruebe en el archivo solo (**protecciones pendientes** ventana)|1.  Cree un nuevo proyecto con un archivo de texto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Desproteger y modificar el archivo de texto.<br />4.  Insertar en el repositorio a través de la **protecciones pendientes** ventana.|Comportamiento esperado común.|  
  
### <a name="case-4b-adding-files"></a>Caso 4b: agregar archivos  
 Al agregar un archivo a un proyecto o un elemento a una solución, debe cambiar también el proyecto o solución. Por lo tanto, el archivo primario también se desprotege y debe estar protegido para completar la adición.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Agregue un archivo de texto y proteger todo (**proteger** cuadro de diálogo)|1.  Cree un nuevo proyecto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Agregue un archivo de texto al proyecto.<br />4.  Aceptar la desprotección del proyecto si se le solicita.<br />5.  Seleccione la solución en **el Explorador de soluciones**.<br />6.  Proteger desde el **proteger** cuadro de diálogo.|Comportamiento esperado común.|  
|Agregue un archivo de texto y proteger todo (**protecciones pendientes** ventana)|1.  Cree un nuevo proyecto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Agregue un archivo de texto al proyecto.<br />4.  Aceptar la desprotección del proyecto si se le solicita.<br />5.  Compruebe en la solución de **protecciones pendientes** ventana.|Comportamiento esperado común|  
  
### <a name="case-4c-adding-projects"></a>Caso 4c: agregar proyectos  
 Al agregar un proyecto a una solución, debe cambiar también la solución. Por lo tanto, el archivo de solución también se desprotege y se debe proteger en para completar la adición.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Agregar un proyecto a una solución bajo control de código fuente en blanco (**proteger** cuadro de diálogo)|1.  Crear una solución en blanco.<br />2.  Agregar la solución al control de código fuente.<br />3.  Agregue un proyecto nuevo.<br />4.  Aceptar la modificación de la solución si se le pide.<br />5.  Proteger desde el **proteger** cuadro de diálogo.|Comportamiento esperado común.|  
|Agregar un proyecto a una solución bajo control de código fuente en blanco (**protecciones pendientes** ventana)|1.  Crear una solución en blanco.<br />2.  Agregar la solución al control de código fuente.<br />3.  Agregue un proyecto nuevo.<br />4.  Aceptar la modificación de la solución si se le pide.<br />5.  Compruebe en la solución de **protecciones pendientes** ventana.|Comportamiento esperado común.|  
  
## <a name="see-also"></a>Vea también  
 [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)