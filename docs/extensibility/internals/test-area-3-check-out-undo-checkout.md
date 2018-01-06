---
title: "Zona de ensayo 3: Check out-Deshacer desprotección | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8835f1f8c312b3aba72353625a1d97b514dc21b8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="test-area-3-check-outundo-checkout"></a>Zona de ensayo 3: Extraer del repositorio / Deshacer desprotección
Esta área de complemento de prueba de control de código fuente cubre los elementos de edición y reversión desde el almacén de versiones a través de la **desproteger** y **Deshacer desprotección** comandos.  
  
 **Extraer del repositorio**: las marcas de un elemento en el almacén de versiones como desprotegido, modifica la copia local a lectura/escritura.  
  
 **Deshacer desprotección**: marca un elemento en el almacén de versiones como protegido, se revierte la copia local al estado anterior a la desprotección (según las opciones).  
  
## <a name="command-menu-access"></a>Acceso al menú de comandos  
 El siguiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] las rutas de acceso del menú de entorno de desarrollo integrado se utilizan en los casos de prueba.  
  
##### <a name="check-out"></a>Check-out:  
  
-   **Archivo**, **Control de código fuente**, **desproteger**.  
  
-   **Archivo**, **desproteger**.  
  
-   Menú contextual, **desproteger**.  
  
-   Deshacer desprotección: **archivo**, **Control de código fuente**, **Deshacer desprotección**.  
  
## <a name="common-expected-behavior"></a>Comportamiento esperado común  
  
-   Después de la operación de desprotección, los archivos de destino y/o las carpetas se marcan como desprotegido en el almacén de versiones.  
  
-   El almacén de versiones atribuye la desprotección al usuario correcto.  
  
-   La fecha y hora de la desprotección son correctos (por la configuración del usuario).  
  
## <a name="test-cases"></a>Casos de prueba  
 Éstos son los casos de prueba concretos para la zona de ensayo de desprotección y Deshacer desprotección.  
  
### <a name="case-3a-check-out"></a>Caso 3a: extraer del repositorio  
 En esta sección se centra en la operación del comando de desprotección.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Comprobar Out exclusivo (COE) un proyecto de cliente|1.  Cree un proyecto de cliente.<br />2.  Agregar la solución al control de código fuente.<br />3.  Desproteger todo el proyecto en modo exclusivo (**archivo**, **desproteger**).|Se produce desprotección.|  
|Extraer del repositorio exclusiva (COE) un sistema de archivos o un proyecto Web de IIS local|1.  Establecer la conexión de servidor Web en el archivo de recurso compartido en **herramientas**, **opciones**, **proyectos**, **configuración Web**.<br />2.  Cree un proyecto web.<br />3.  Agregar la solución al control de código fuente.<br />4.  Desproteger todo el proyecto en modo exclusivo (**archivo**, **Control de código fuente**, **desproteger**).|Se produce desprotección.|  
|Desproteger elementos de la solución en una solución (nuevo método para controlar otros archivos)|1.  Crear una solución en blanco.<br />2.  Agregar la solución al control de código fuente.<br />3.  Desproteger la solución.<br />4.  Agregar varios elementos de la solución.<br />5.  Compruebe todos los elementos recién agregados.<br />6.  Seleccionar varios elementos de la solución.<br />7.  Extraer del repositorio los elementos seleccionados (menú contextual, **desproteger**).|Archivos seleccionados se desprotegen.|  
|Desproteger versión Local (si el complemento sometida a prueba es compatible con esta característica)|1.  El usuario 1: Crear un proyecto de cliente.<br />2.  El usuario 1: Agregar la solución al control de código fuente.<br />3.  El usuario 2: Abra la solución de control de código fuente a otra ubicación.<br />4.  El usuario 2: Desproteger un archivo.<br />5.  El usuario 2: Modificar el archivo.<br />6.  El usuario 2: Revise el archivo.<br />7.  Usuario 1: Desproteger la versión local del archivo (comprobar la **Desproteger versión Local** opción en avanzada **desproteger** cuadro de diálogo).|La versión local del archivo se desprotege.<br /><br /> Las modificaciones por el usuario 2 no se aplican al archivo de usuario 1.|  
  
### <a name="case-3b-disconnected-check-out"></a>Caso 3b: desconectado de desprotección  
 Funciona en modo sin conexión permite a los usuarios cierto nivel de compatibilidad con el control continuo de origen cuando no está conectado directamente a un almacén de versiones. Para ello, almacenamiento en caché local de toda la información relevante acerca de la solución dada de alta y proyectos.  
  
 Las operaciones de desprotección exclusiva sólo puede ocurrir mientras se está conectado en el almacén de control de código fuente. Las operaciones de desprotección compartida puede producirse en cualquier momento, ya sea conectado o desconectado. Por lo tanto, cuando se desconecta el almacén de versiones, solo el **comprobar compartido** (CO) comando está habilitado. Mientras está desconectada, **Deshacer desprotección** está deshabilitada porque no se puede recuperar la versión anterior para reemplazar los cambios realizados por el usuario.  
  
 Cuando el usuario vuelve a conectarse a la versión almacena, los Estados de desprotección de todas las soluciones dada de alta y se sincronizan los proyectos. Esto realiza las actualizaciones necesarias en el almacén de las desprotecciones que ha realizado el usuario. Una vez que se ha producido la sincronización, el usuario es capaz de seguir trabajando como normal (conectado).  
  
#### <a name="expected-behavior"></a>Comportamiento esperado  
  
-   No se puede usar **comprobar exclusivamente** comando mientras se está desconectado del almacén de versiones.  
  
-   No se puede usar **Deshacer desprotección** comando mientras se está desconectado del almacén de versiones.  
  
-   **Compartido desproteger** comando funciona.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Mientras está desconectada, desproteger un archivo, a continuación, conectarse para la sincronización|1.  Desconectar un proyecto controlado mediante el cuadro de diálogo de Control de código fuente de cambio (**archivo**, **Control de código fuente**, **Cambiar control de código fuente**l).<br />2.  Desproteger un archivo.<br />3.  Haga clic en extraer del repositorio (desconectado) en el cuadro de diálogo de advertencia.<br />4.  Edite el archivo.<br />5.  Conectarse mediante el cuadro de diálogo Cambiar Control de código fuente.<br />6.  Obtener la versión más reciente del archivo editado.|Comportamiento esperado común|  
  
### <a name="case-3c-query-editquery-save-qeqs"></a>Caso 3C: Editar consulta/guardar (QEQS)  
 Se realiza un seguimiento de los elementos bajo control de código fuente para ediciones, cambios, y guarda ayudar fácilmente a los usuarios administrar sus archivos. Cuando se edita un elemento controlado que está "protegido", QEQS intercepta la edición ha intentado y se pregunta al usuario si desea desproteger el archivo para editarlo. En función de **herramientas**, **opciones** configuración, el usuario es exige la comprobación desproteger el archivo para editar, o bien, puede tener permiso para editar una copia en memoria y extraer del repositorio más adelante. Si el usuario **herramientas**, **opciones** valor no está establecido para mostrar el cuadro de diálogo de desprotección y simplemente Eche un vistazo, a continuación, a medida que el usuario hace su edición, el archivo desprotege automáticamente, siempre que sea posible.  
  
#### <a name="expected-behavior"></a>Comportamiento esperado  
  
-   Después de la operación de desprotección, los archivos de destino y/o las carpetas se marcan como desprotegido en el almacén de versiones.  
  
-   El almacén de versiones atribuye la desprotección al usuario correcto.  
  
-   La fecha y hora de la desprotección son correctos (por la configuración del usuario).  
  
-   La copia local del archivo de destino o la carpeta es grabable.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Editar el archivo de texto que está protegido en|1.  Cree un nuevo proyecto que contiene un archivo de texto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Establecer **herramientas**, **opciones**, **Control de código fuente**, **permite que se pueden editar mientras solo lectura en el disco archivos** a desactivada.<br />4.  Establecer **herramientas**, **opciones**, **Control de código fuente**, **Preguntar para desproteger** en la **cuando se activa archivos soneditado** cuadro combinado.<br />5.  Establecer **herramientas**, **opciones**, **Control de código fuente**, **Preguntar para desproteger** en la **cuando se activa los archivos se guardan** cuadro combinado.<br />6.  Abra el archivo de texto en el editor, intentar escribir el nuevo texto en el archivo. Si este paso se realiza correctamente, vaya al paso siguiente.<br />7.  Haga clic en **cancelar** en el **desproteger para editar** cuadro de diálogo. Si este paso se realiza correctamente, vaya al paso siguiente.<br />8.  Establecer **herramientas**, **opciones**, **Control de código fuente**, **permite que se pueden editar mientras solo lectura en el disco archivos** a comprobado.<br />9. Abra el archivo de proyecto en el editor, intenta escribir texto nuevo en el archivo. Si este paso se realiza correctamente, vaya al paso siguiente.<br />10. Haga clic en **editar** en el **desproteger para editar** cuadro de diálogo. Si este paso se realiza correctamente, vaya al paso siguiente.<br />11. Editar el archivo de texto e intentar guardarlo.|`Result of step 6:`<br /><br /> Extraer del repositorio para aparece el cuadro de diálogo de edición.<br /><br /> `Result of step 7:`<br /><br /> El archivo no se modifica.<br /><br /> `Result of step 9:`<br /><br /> Extraer del repositorio para aparece el cuadro de diálogo de edición.<br /><br /> `Result of step 10:`<br /><br /> Puede editar el archivo de proyecto en la memoria.<br /><br /> `Result of step 11:`<br /><br /> En Guardar, aparece la desprotección en cuadro de diálogo Guardar.|  
|Editar un archivo de solución que está protegido|Repita los pasos tal como se describe anteriormente en prueban, pero en lugar de modificar un archivo de texto, modificar soluciones mediante el cambio de propiedades de la solución.|Igual que la prueba anterior|  
|Editar un archivo de proyecto que está protegido|Repita los pasos tal como se describe anteriormente en la prueba, pero en lugar de modificar un archivo de texto, modificar el proyecto cambiando las propiedades del proyecto.|Igual que la prueba anterior.|  
  
### <a name="case-3d-silent-check-out"></a>Mayúsculas y minúsculas 3d: Silenciosa desprotección  
 Esta comprobación de portadas subárea escenarios donde la **desproteger** cuadro de diálogo no aparece del usuario **herramientas**, **opciones**, **configuración de Control de código fuente** .  
  
#### <a name="expected-behavior"></a>Comportamiento esperado  
  
-   Después de la operación de desprotección, los archivos de destino y/o las carpetas se marcan como desprotegido en el almacén de versiones.  
  
-   El almacén de versiones atribuye la desprotección al usuario correcto.  
  
-   La fecha y hora de la modificación es correcta (según la configuración del usuario).  
  
-   La copia local del archivo de destino o la carpeta es grabable.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Extracción del repositorio silenciosa para un archivo|1.  Establecer **herramientas**, **opciones**, **Control de código fuente** a **archivos de desprotección automáticamente en Editar**.<br />2.  Cree un nuevo proyecto con un archivo.<br />3.  Agregar la solución al control de código fuente.<br />4.  Desproteger el archivo.|Archivo se desprotege de forma silenciosa (sin interfaz de usuario).|  
|Extracción del repositorio silenciosa para un proyecto|1.  Establecer **herramientas**, **opciones**, **Control de código fuente** a **archivos de desprotección automáticamente en Editar**.<br />2.  Cree un nuevo proyecto.<br />3.  Agregar la solución al control de código fuente.<br />4.  Desproteger el proyecto.|Archivo se desprotege de forma silenciosa (sin interfaz de usuario).|  
  
### <a name="case-3e-undo-check-out"></a>Caso 3e: extraer del repositorio  
 **Deshacer desprotección** se utiliza para cancelar un archivo desprotegido estado y evitar la comprobación de los cambios realizados en el archivo.  
  
#### <a name="expected-behavior"></a>Comportamiento esperado  
  
-   El valor predeterminado se basa en el usuario **desproteger la versión Local** configuración. Si el usuario ha elegido desproteger la versión local, el valor predeterminado para la desprotección es siempre volverá a la versión que desprotegió.  
  
-   Tras la aceptación de la reversión, los iconos de **el Explorador de soluciones** se actualizan para afectados archivos y el elemento se quita de la **protecciones pendientes** ventana.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Deshacer desprotección de un único archivo que está desprotegido exclusivamente|1.  Cree un proyecto de cliente.<br />2.  Agregar la solución al control de código fuente.<br />3.  Desprotege un archivo en modo exclusivo.<br />4.  Modificar el archivo.<br />5.  Deshacer desprotección (**archivo**, **Control de código fuente**, **Deshacer desprotección**).|Comportamiento esperado común.|  
|Deshacer desprotección de un único archivo que está desprotegido compartido|1.  Cree un proyecto de cliente.<br />2.  Agregar la solución al control de código fuente.<br />3.  Desproteger un archivo compartido.<br />4.  Modificar el archivo.<br />5.  Deshacer desprotección (**archivo**, **Control de código fuente**, **Deshacer desprotección**).|Comportamiento esperado común.|  
|Deshacer desprotección de un proyecto después de agregar archivos al proyecto|1.  Cree un nuevo proyecto y agregarlo al control de código fuente.<br />2.  Desproteger el proyecto.<br />3.  Agregue un archivo al proyecto.<br />4.  Deshacer desprotección del proyecto.|Archivo agregado se quita del proyecto en el Explorador de soluciones.<br /><br /> Proyecto ya no está desprotegido.|  
|Deshacer desprotección de un proyecto después de eliminar los archivos del proyecto|1.  Cree un nuevo proyecto y agregarlo al control de código fuente.<br />2.  Desproteger el proyecto.<br />3.  Elimine un archivo del proyecto.<br />4.  Deshacer desprotección del proyecto.|Archivo eliminado aparece bajo el proyecto en el Explorador de soluciones.<br /><br /> Proyecto ya no está desprotegido.|  
  
## <a name="see-also"></a>Vea también  
 [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)