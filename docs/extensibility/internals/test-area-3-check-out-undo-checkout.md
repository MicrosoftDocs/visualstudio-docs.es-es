---
title: "&#193;rea de prueba 3: Comprobaci&#243;n de out-Deshacer desprotecci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "los complementos de control de código fuente, la desprotección"
  - "Deshacer desprotección, complementos de control de origen"
  - "control de código fuente [Visual Studio SDK], desproteger"
  - "Deshacer desprotección de control [Visual Studio SDK], de origen"
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# &#193;rea de prueba 3: Desproteger o deshacer desprotecci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta área de complemento de prueba de control de código fuente cubre los elementos de edición y reversión del almacén de versiones a través de la **Desproteger** y **Deshacer desprotección** comandos.  
  
 **Desproteger**: las marcas de un elemento en el almacén de versiones como desprotegido, modifica la copia local para lectura y escritura.  
  
 **Deshacer desprotección**: marca un elemento en el almacén de versiones como protegido, se revierte la copia local al estado antes de la extracción \(según las opciones\).  
  
## Acceso al menú de comandos  
 La siguiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rutas de menú del entorno de desarrollo integrado se utilizan en los casos de prueba.  
  
##### Consulte:  
  
-   **Archivo**, **Control de código fuente**, **Desproteger**.  
  
-   **Archivo**, **Desproteger**.  
  
-   Menú contextual, **Desproteger**.  
  
-   Deshacer desprotección: **archivo**, **Control de código fuente**, **Deshacer desprotección**.  
  
## Comportamiento esperado comunes  
  
-   Después de la operación de desprotección, los archivos de destino o las carpetas se marcan como desprotegidos en el almacén de versiones.  
  
-   El almacén de versiones atributos la desprotección al usuario correcto.  
  
-   La fecha y hora de la desprotección son correctos \(según la configuración del usuario\).  
  
## Casos de prueba  
 Los siguientes son los casos de prueba concretos para la zona de ensayo de desprotección y Deshacer desprotección.  
  
### Caso 3a: desproteger  
 En esta sección se centra en la operación del comando de desprotección.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|---------------------|-----------------------------------------|  
|Compruebe las exclusivo \(COE\) un proyecto de cliente|1.  Cree un proyecto de cliente.<br />2.  Agregar la solución al control de código fuente.<br />3.  Desproteger todo el proyecto en modo exclusivo \(**archivo**, **Desproteger**\).|Se produce desprotección.|  
|Desproteger en exclusiva \(COE\) un sistema de archivos o un proyecto Web de IIS local|1.  Establecer la conexión de servidor Web en el archivo de recurso compartido en **herramientas**, **opciones**, **proyectos**, **configuración Web**.<br />2.  Cree un proyecto Web.<br />3.  Agregar la solución al control de código fuente.<br />4.  Desproteger todo el proyecto en modo exclusivo \(**archivo**, **Control de código fuente**, **Desproteger**\).|Se produce desprotección.|  
|Desproteger elementos de la solución en una solución \(nuevo método para controlar otros archivos\)|1.  Crear una solución en blanco.<br />2.  Agregar la solución al control de código fuente.<br />3.  Desproteger la solución.<br />4.  Agregar varios elementos de la solución.<br />5.  Compruebe todos los elementos recién agregados.<br />6.  Seleccionar varios elementos de la solución.<br />7.  Desproteger los elementos seleccionados \(menú contextual, **Desproteger**\).|Los archivos seleccionados están desprotegidos.|  
|Desproteger versión Local \(si el complemento está probando admite esta característica\)|1.  El usuario 1: Crear un proyecto de cliente.<br />2.  El usuario 1: Agregar la solución al control de código fuente.<br />3.  El usuario 2: Abra la solución de control de código fuente a otra ubicación.<br />4.  El usuario 2: Desproteger un archivo.<br />5.  El usuario 2: Modificar el archivo.<br />6.  El usuario 2: Proteger el archivo.<br />7.  El usuario 1: Desproteger la versión local del archivo \(comprobar la **Desproteger versión Local** opción en avanzada **Desproteger** cuadro de diálogo\).|La versión local del archivo se desprotege.<br /><br /> Las modificaciones por el usuario 2 no se aplican al archivo de usuario 1.|  
  
### Caso 3b: desconectado de desprotección  
 Funciona en modo sin conexión permite a los usuarios en algún nivel de compatibilidad con el control continuo del origen cuando no está conectado directamente a un almacén de versiones. Para ello, almacenamiento en caché local de toda la información pertinente acerca de los proyectos y soluciones dada de alta.  
  
 Las operaciones de desprotección exclusiva sólo puede realizarse mientras está conectado en el almacén de control de código fuente. Las operaciones de desprotección compartida puede producirse en cualquier momento, ya sea conectado o desconectado. Por lo tanto, cuando desconecta el almacén de versiones, sólo el **Comprobar compartido** \(comando está habilitado COS\). Mientras está desconectado, **Deshacer desprotección** está deshabilitado porque no se puede recuperar la versión anterior para reemplazar los cambios realizados por el usuario.  
  
 Cuando el usuario vuelve a conectarse a la versión almacenar los Estados de desprotección de todas las soluciones dadas de alta y se sincronizan los proyectos. Esto realiza las actualizaciones necesarias en el almacén para las desprotecciones realizadas por el usuario. Una vez que se ha producido la sincronización, el usuario es capaz de seguir trabajando como normal \(conectado\).  
  
#### Comportamiento esperado  
  
-   No se puede usar **Comprobar exclusivamente** comando mientras está desconectado del almacén de versiones.  
  
-   No se puede usar **Deshacer desprotección** comando mientras está desconectado del almacén de versiones.  
  
-   **Compartido desproteger** comando funciona.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|---------------------|-----------------------------------------|  
|Mientras está desconectado, desproteger un archivo y después conectar para la sincronización|1.  Desconectar un proyecto controlado mediante el cuadro de diálogo Cambiar Control de código fuente \(**archivo**, **Control de código fuente**, **Cambiar control de código fuente**l\).<br />2.  Desproteger un archivo.<br />3.  Haga clic en Desproteger \(sin conexión\) en el cuadro de diálogo de advertencia.<br />4.  Edite el archivo.<br />5.  Conectar mediante el cuadro de diálogo Cambiar Control de código fuente.<br />6.  Obtener la versión más reciente del archivo modificado.|Comportamiento esperado comunes|  
  
### Caso 3c: consulta edición guarde \(QEQS\)  
 Se realiza un seguimiento de los elementos bajo control de código fuente para ediciones, cambios, y guarda para ayudar a fácilmente a los usuarios administrar sus archivos. Cuando se edita un elemento controlado "protegido", QEQS intercepta la edición ha intentado y pregunta al usuario si desea desproteger el archivo para editarlo. En función de **herramientas**, **opciones** configuración, el usuario es exige la comprobación desproteger el archivo para editar, o bien, puede tener permiso para editar una copia en memoria y consulte más adelante. Si el usuario **herramientas**, **opciones** valor no está establecido para mostrar el cuadro de diálogo de desprotección y simplemente desprotegerlo, a continuación, cuando el usuario hace su edición, el archivo desprotege automáticamente, siempre que sea posible.  
  
#### Comportamiento esperado  
  
-   Después de la operación de desprotección, los archivos de destino o las carpetas se marcan como desprotegidos en el almacén de versiones.  
  
-   El almacén de versiones atributos la desprotección al usuario correcto.  
  
-   La fecha y hora de la desprotección son correctos \(según la configuración del usuario\).  
  
-   La copia local del archivo de destino o la carpeta es grabable.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|---------------------|-----------------------------------------|  
|Editar el archivo de texto que está protegido|1.  Cree un nuevo proyecto que contiene un archivo de texto.<br />2.  Agregar la solución al control de código fuente.<br />3.  Establecer **herramientas**, **opciones**, **Control de código fuente**, **Permitir pueden editar mientras de sólo lectura de archivos** a desactivada.<br />4.  Establecer **herramientas**, **opciones**, **Control de código fuente**, **Preguntar para desproteger** en el **cuando proteja los archivos se editan** cuadro combinado.<br />5.  Establecer **herramientas**, **opciones**, **Control de código fuente**, **Preguntar para desproteger** en el **cuando proteja los archivos se guardan** cuadro combinado.<br />6.  Abra el archivo de texto en el editor, intentar escribir texto nuevo en el archivo. Si este paso se realiza correctamente, vaya al paso siguiente.<br />7.  Haga clic en **Cancelar** en el **Desproteger para editar** cuadro de diálogo. Si este paso se realiza correctamente, vaya al paso siguiente.<br />8.  Establecer **herramientas**, **opciones**, **Control de código fuente**, **Permitir pueden editar mientras de sólo lectura de archivos** a activado.<br />9. Abra el archivo de proyecto en el editor, intente escribir texto nuevo en el archivo. Si este paso se realiza correctamente, vaya al paso siguiente.<br />10. Haga clic en **Editar** en el **Desproteger para editar** cuadro de diálogo. Si este paso se realiza correctamente, vaya al paso siguiente.<br />11. Editar el archivo de texto e intente guardarlo.|`Result of step 6:`<br /><br /> Desproteger para aparece el cuadro de diálogo de edición.<br /><br /> `Result of step 7:`<br /><br /> El archivo no se modifica.<br /><br /> `Result of step 9:`<br /><br /> Desproteger para aparece el cuadro de diálogo de edición.<br /><br /> `Result of step 10:`<br /><br /> Puede editar el archivo de proyecto en la memoria.<br /><br /> `Result of step 11:`<br /><br /> En Guardar, aparece la desprotección en cuadro de diálogo Guardar.|  
|Editar un archivo de solución que está protegido|Repita los pasos tal como se describe anteriormente en prueban, pero en lugar de modificar un archivo de texto, modificación la solución cambiando las propiedades de la solución.|Igual que la prueba anterior|  
|Editar un archivo de proyecto que está protegido|Repita los pasos tal como se describe anteriormente en prueban, pero en lugar de modificar un archivo de texto, modificación el proyecto cambiando las propiedades del proyecto.|Igual que la prueba anterior.|  
  
### Mayúsculas y minúsculas 3d: Silencioso desprotección  
 Esta comprobación de subárea abarca escenarios donde el **Desproteger** cuadro de diálogo no aparece por de usuario **herramientas**, **opciones**, **configuración de Control de código fuente**.  
  
#### Comportamiento esperado  
  
-   Después de la operación de desprotección, los archivos de destino o las carpetas se marcan como desprotegidos en el almacén de versiones.  
  
-   El almacén de versiones atributos la desprotección al usuario correcto.  
  
-   La fecha y hora de la desprotección es correcto \(según la configuración del usuario\).  
  
-   La copia local del archivo de destino o la carpeta es grabable.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|---------------------|-----------------------------------------|  
|Retirada silenciosa para un archivo|1.  Establecer **herramientas**, **opciones**, **Control de código fuente** a **archivos desprotección automáticamente en Editar**.<br />2.  Cree un nuevo proyecto con un archivo.<br />3.  Agregar la solución al control de código fuente.<br />4.  Desproteger el archivo.|Archivo se desprotege de forma silenciosa \(sin interfaz de usuario\).|  
|Retirada silenciosa para un proyecto|1.  Establecer **herramientas**, **opciones**, **Control de código fuente** a **archivos desprotección automáticamente en Editar**.<br />2.  Cree un nuevo proyecto.<br />3.  Agregar la solución al control de código fuente.<br />4.  Desproteger el proyecto.|Archivo se desprotege de forma silenciosa \(sin interfaz de usuario\).|  
  
### Caso 3e: Deshacer desprotección  
 **Deshacer desprotección** se utiliza para cancelar un archivo desprotegido por estado y evitar la comprobación de los cambios realizados en el archivo.  
  
#### Comportamiento esperado  
  
-   El valor predeterminado se basa en el usuario **Desproteger la versión Local** configuración. Si el usuario ha elegido desproteger la versión local, el valor predeterminado para la desprotección es siempre volverá a la versión que desprotegió.  
  
-   Tras la recepción de la acción de deshacer, los iconos de **el Explorador de soluciones** se actualizan para afectados archivos y el elemento se quita de la **protecciones pendientes** ventana.  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|---------------------|-----------------------------------------|  
|Deshacer la desprotección de un único archivo que está desprotegido en exclusiva|1.  Cree un proyecto de cliente.<br />2.  Agregar la solución al control de código fuente.<br />3.  Desprotege un archivo en modo exclusivo.<br />4.  Modificar el archivo.<br />5.  Deshacer desprotección \(**archivo**, **Control de código fuente**, **Deshacer desprotección**\).|Comportamiento esperado común.|  
|Deshacer la desprotección de un único archivo que está desprotegido compartido|1.  Cree un proyecto de cliente.<br />2.  Agregar la solución al control de código fuente.<br />3.  Desproteger un archivo compartido.<br />4.  Modificar el archivo.<br />5.  Deshacer desprotección \(**archivo**, **Control de código fuente**, **Deshacer desprotección**\).|Comportamiento esperado común.|  
|Deshacer desprotección de un proyecto después de agregar archivos al proyecto|1.  Cree un nuevo proyecto y agregar al control de código fuente.<br />2.  Desproteger el proyecto.<br />3.  Agregue un archivo al proyecto.<br />4.  Deshacer la desprotección del proyecto.|Archivo agregado se quita del proyecto en el Explorador de soluciones.<br /><br /> Proyecto ya no está desprotegido.|  
|Deshacer desprotección de un proyecto después de eliminar los archivos del proyecto|1.  Cree un nuevo proyecto y agregar al control de código fuente.<br />2.  Desproteger el proyecto.<br />3.  Eliminar un archivo del proyecto.<br />4.  Deshacer la desprotección del proyecto.|Archivo eliminado aparece bajo el proyecto en el Explorador de soluciones.<br /><br /> Proyecto ya no está desprotegido.|  
  
## Vea también  
 [Guía de pruebas para los complementos de Control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)