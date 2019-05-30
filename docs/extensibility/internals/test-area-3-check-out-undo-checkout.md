---
title: 'Área de prueba 3: Check out-Deshacer desprotección | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93ca3f2c656c6bea81139e5e6101499a7fc8febd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331066"
---
# <a name="test-area-3-check-outundo-checkout"></a>Área de prueba 3: Desproteger o deshacer desprotección
Esta área de prueba de complemento de control de código fuente trata los elementos de edición y revertir desde el almacén de versiones a través de la **desproteger** y **Deshacer desprotección** comandos.

**Consulte**: Las marcas de un elemento en el almacén de versiones como desprotegido, modifica la copia local de lectura/escritura.

**Deshacer desprotección**: Las marcas de un elemento en el almacén de versiones como protegido, revierte la copia local al estado antes de la desprotección (según las opciones).

## <a name="command-menu-access"></a>Acceso al menú de comandos

La siguiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rutas de menú del entorno de desarrollo integrado que se usan en los casos de prueba.

##### <a name="check-out"></a>Check-out:

- **Archivo**, **Control de código fuente**, **desproteger**.

- **Archivo**, **desproteger**.

- Menú contextual, **desproteger**.

- Deshacer desprotección: **Archivo**, **Control de código fuente**, **Deshacer desprotección**.

## <a name="common-expected-behavior"></a>Comportamiento esperado comunes

- Después de la operación de desprotección, los archivos de destino o las carpetas se marcan como desprotegidos en el almacén de versiones.

- El almacén de versiones de la desprotección atributos para el usuario correcto.

- La fecha y hora de la desprotección son correctos (según la configuración del usuario).

## <a name="test-cases"></a>Casos de prueba

Los siguientes son casos de prueba concretos para el área de prueba de desprotección y la desprotección.

### <a name="case-3a-check-out"></a>Case 3a: Desproteger

En esta sección se centra en la operación del comando de desprotección.

|Acción|Pasos de prueba|Resultados esperados para comprobar|
|------------|----------------|--------------------------------|
|Comprobar salida exclusivo (COE) un proyecto de cliente|1.  Cree un proyecto de cliente.<br />2.  Agregue la solución al control de código fuente.<br />3.  Desproteger todo el proyecto en modo exclusivo (**archivo**, **desproteger**).|Se produce desprotección.|
|Desproteger en exclusiva (COE) un sistema de archivos o un proyecto Web de IIS local|1.  Establecer la conexión de servidor Web en el archivo de recurso compartido en **herramientas**, **opciones**, **proyectos**, **configuración Web**.<br />2.  Cree un proyecto web.<br />3.  Agregue la solución al control de código fuente.<br />4.  Desproteger todo el proyecto en modo exclusivo (**archivo**, **Control de código fuente**, **desproteger**).|Se produce desprotección.|
|Revise los elementos de la solución en una solución (nuevo método para controlar otros archivos)|1.  Crear una solución en blanco.<br />2.  Agregue la solución al control de código fuente.<br />3.  Desproteger la solución.<br />4.  Agregar varios elementos de la solución.<br />5.  Compruebe todos los elementos recién agregados.<br />6.  Seleccionar varios elementos de la solución.<br />7.  Desprotege los elementos seleccionados (menú contextual, **desproteger**).|Los archivos seleccionados están desprotegidos.|
|Desproteger versión Local (si el complemento sometida a prueba es compatible con esta característica)|1.  Usuario 1: Cree un proyecto de cliente.<br />2.  Usuario 1: Agregue la solución al control de código fuente.<br />3.  Usuario 2: Abra la solución del control de código fuente a otra ubicación.<br />4.  Usuario 2: Desproteger un archivo.<br />5.  Usuario 2: Modifique el archivo.<br />6.  Usuario 2: Revise el archivo.<br />7.  Usuario 1: Desproteger versión local del archivo (Compruebe la **Desproteger versión Local** opción en avanzada **desproteger** cuadro de diálogo).|Versión local del archivo está desprotegido.<br /><br /> Las modificaciones por el usuario 2 no se aplican al archivo de 1 usuario.|

### <a name="case-3b-disconnected-check-out"></a>Escenario 3b: Desproteger desconectado

Funciona en modo sin conexión permite a los usuarios cierto nivel de compatibilidad con el control continuo del origen cuando no está conectado directamente a un almacén de versiones. Esto se hace almacenando en caché localmente a toda la información relevante acerca de los proyectos y soluciones dada de alta.

Las operaciones de desprotección exclusiva sólo puede realizarse mientras está conectado al almacén de control de código fuente. Las operaciones de desprotección compartida puede producirse en cualquier momento, ya sea conectado o desconectado. Por lo tanto, cuando desconecta el almacén de versiones, solo el **comprobar compartido** (CO) comando está habilitado. Mientras está desconectado, **Deshacer desprotección** está deshabilitada porque no se puede recuperar la versión anterior para reemplazar los cambios realizados por el usuario.

Cuando el usuario vuelve a conectarse a la versión de almacenar los Estados de desprotección de todas las soluciones dada de alta y se sincronizan los proyectos. Esto realiza las actualizaciones necesarias en el almacén para las desprotecciones que ha realizado el usuario. Una vez que se ha producido la sincronización, el usuario es capaz de seguir trabajando como normal (conectado).

#### <a name="expected-behavior"></a>Comportamiento esperado

- No se puede usar **comprobar exclusivamente** comando mientras está desconectado del almacén de versiones.

- No se puede usar **Deshacer desprotección** comando mientras está desconectado del almacén de versiones.

- **Compartido desproteger** comando funciona.

|Acción|Pasos de prueba|Resultados esperados para comprobar|
|------------|----------------|--------------------------------|
|Mientras está desconectado, desproteger un archivo y luego conectarse para la sincronización|1.  Desconectar un proyecto controlado mediante el cuadro de diálogo Cambiar Control de código (**archivo**, **Control de código fuente**, **cambiar Control de código fuente**).<br />2.  Desproteger un archivo.<br />3.  Haga clic en Desproteger (sin conexión) en el cuadro de diálogo de advertencia.<br />4.  Edite el archivo.<br />5.  Conectarse mediante el cuadro de diálogo Cambiar Control de código fuente.<br />6.  Obtener la versión más reciente del archivo modificado.|Comportamiento esperado comunes|

### <a name="case-3c-query-editquery-save-qeqs"></a>Caso 3C: Edición de consulta o consulta guardar (QEQS)
 Se realiza un seguimiento de los elementos bajo control de código fuente para las ediciones, cambios, y se guarda para ayudar con facilidad a los usuarios administrar sus archivos. Cuando se modifica un elemento controlado que es "protegido", QEQS intercepta la edición de intentada y pide al usuario si desea desproteger el archivo para editarlo. En función de **herramientas**, **opciones** settings, el usuario es exige la comprobación desproteger el archivo para editar, o bien, es posible que se pueden editar una copia en memoria y consultar más adelante. Si el usuario **herramientas**, **opciones** configuración no está establecida para mostrar el cuadro de diálogo de desprotección y sólo Eche un vistazo, como el usuario realiza su edición, el archivo desprotege automáticamente, siempre que sea posible.

#### <a name="expected-behavior"></a>Comportamiento esperado

- Después de la operación de desprotección, los archivos de destino o las carpetas se marcan como desprotegidos en el almacén de versiones.

- El almacén de versiones de la desprotección atributos para el usuario correcto.

- La fecha y hora de la desprotección son correctos (según la configuración del usuario).

- La copia local de la carpeta o archivo de destino es grabable.

|Acción|Pasos de prueba|Resultados esperados para comprobar|
|------------|----------------|--------------------------------|
|Editar el archivo de texto que está protegido|1.  Cree un nuevo proyecto que contiene un archivo de texto.<br />2.  Agregue la solución al control de código fuente.<br />3.  Establecer **herramientas**, **opciones**, **Control de código fuente**, **permitir que los archivos se puede editar mientras de solo lectura en disco** a desactivada.<br />4.  Establecer **herramientas**, **opciones**, **Control de código fuente**, **Preguntar para desproteger** en el **cuando está activada los archivos soneditado** cuadro combinado.<br />5.  Establecer **herramientas**, **opciones**, **Control de código fuente**, **Preguntar para desproteger** en el **cuando está activada los archivos se guardan** cuadro combinado.<br />6.  Abra el archivo de texto en el editor, intentar escribir texto nuevo en el archivo. Si este paso se realiza correctamente, vaya al paso siguiente.<br />7.  Haga clic en **cancelar** en el **desproteger para editar** cuadro de diálogo. Si este paso se realiza correctamente, vaya al paso siguiente.<br />8.  Establecer **herramientas**, **opciones**, **Control de código fuente**, **permitir que los archivos se puede editar mientras de solo lectura en disco** a activado.<br />9. Abra el archivo de proyecto en el editor, intentar escribir texto nuevo en el archivo. Si este paso se realiza correctamente, vaya al paso siguiente.<br />10. Haga clic en **editar** en el **desproteger para editar** cuadro de diálogo. Si este paso se realiza correctamente, vaya al paso siguiente.<br />11. Edite el archivo de texto e intentar guardarlo.|`Result of step 6:`<br /><br /> Desproteger para aparece el cuadro de diálogo de edición.<br /><br /> `Result of step 7:`<br /><br /> No se modifica el archivo.<br /><br /> `Result of step 9:`<br /><br /> Desproteger para aparece el cuadro de diálogo de edición.<br /><br /> `Result of step 10:`<br /><br /> Puede editar el archivo de proyecto en la memoria.<br /><br /> `Result of step 11:`<br /><br /> En Guardar, aparece la desprotección en cuadro de diálogo Guardar.|
|Editar un archivo de solución que está protegido|Repita los pasos tal como se describe en el anterior de prueba, pero en lugar de modificar un archivo de texto, modificar la solución cambiando las propiedades de la solución.|Igual que la prueba anterior|
|Editar un archivo de proyecto que está protegido|Repita los pasos tal como se describe en el anterior de prueba, pero en lugar de modificar un archivo de texto, modifique el proyecto cambiando las propiedades del proyecto.|Igual que la prueba anterior.|

### <a name="case-3d-silent-check-out"></a>Caso 3d: Desproteger silenciosa
 Esta comprobación de segundo plano subárea escenarios donde el **desproteger** cuadro de diálogo no aparece por usuario **herramientas**, **opciones**, **configuración de Control de código fuente** .

#### <a name="expected-behavior"></a>Comportamiento esperado

- Después de la operación de desprotección, los archivos de destino o las carpetas se marcan como desprotegidos en el almacén de versiones.

- El almacén de versiones de la desprotección atributos para el usuario correcto.

- La fecha y hora de la desprotección es correcto (según la configuración del usuario).

- La copia local de la carpeta o archivo de destino es grabable.

|Acción|Pasos de prueba|Resultados esperados para comprobar|
|------------|----------------|--------------------------------|
|Retirada silenciosa para un archivo|1.  Establecer **herramientas**, **opciones**, **Control de código fuente** a **extraer archivos automáticamente en Editar**.<br />2.  Cree un nuevo proyecto con un archivo.<br />3.  Agregue la solución al control de código fuente.<br />4.  Desproteger el archivo.|Archivo se desprotege de forma silenciosa (sin interfaz de usuario).|
|Retirada silenciosa para un proyecto|1.  Establecer **herramientas**, **opciones**, **Control de código fuente** a **extraer archivos automáticamente en Editar**.<br />2.  Cree un nuevo proyecto.<br />3.  Agregue la solución al control de código fuente.<br />4.  Extraer del repositorio el proyecto.|Archivo se desprotege de forma silenciosa (sin interfaz de usuario).|

### <a name="case-3e-undo-check-out"></a>Case 3e: Deshacer desprotección
 **Deshacer desprotección** se utiliza para cancelar un archivo desprotegido por estado y evitar la comprobación de los cambios realizados en el archivo.

#### <a name="expected-behavior"></a>Comportamiento esperado

- El valor predeterminado se basa en el usuario **Desproteger versión Local** configuración. Si el usuario ha elegido Desproteger versión local, el valor predeterminado de la desprotección es siempre volverá a la versión que desprotegió.

- Tras la aceptación de la fase de reversión, los iconos de **el Explorador de soluciones** se actualizan para afectados los archivos y el elemento se quita de la **protecciones pendientes** ventana.

|Acción|Pasos de prueba|Resultados esperados para comprobar|
|------------|----------------|--------------------------------|
|Deshacer desprotección de un único archivo que está desprotegido en exclusiva|1.  Cree un proyecto de cliente.<br />2.  Agregue la solución al control de código fuente.<br />3.  Desproteger un archivo de forma exclusiva.<br />4.  Modifique el archivo.<br />5.  Deshacer desprotección (**archivo**, **Control de código fuente**, **Deshacer desprotección**).|Comportamiento esperado común.|
|Deshacer desprotección de un único archivo que está desprotegido compartido|1.  Cree un proyecto de cliente.<br />2.  Agregue la solución al control de código fuente.<br />3.  Desproteger un archivo compartido.<br />4.  Modifique el archivo.<br />5.  Deshacer desprotección (**archivo**, **Control de código fuente**, **Deshacer desprotección**).|Comportamiento esperado común.|
|Deshacer desprotección de un proyecto después de agregar archivos al proyecto|1.  Cree un nuevo proyecto y agregarlo al control de código fuente.<br />2.  Extraer del repositorio el proyecto.<br />3.  Agregue un archivo al proyecto.<br />4.  Deshacer desprotección del proyecto.|Archivo agregado se quitó del proyecto en el Explorador de soluciones.<br /><br /> Proyecto ya no está desprotegido.|
|Deshacer desprotección de un proyecto después de eliminar los archivos del proyecto|1.  Cree un nuevo proyecto y agregarlo al control de código fuente.<br />2.  Extraer del repositorio el proyecto.<br />3.  Eliminar un archivo del proyecto.<br />4.  Deshacer desprotección del proyecto.|Archivo eliminado aparece bajo el proyecto en el Explorador de soluciones.<br /><br /> Proyecto ya no está desprotegido.|

## <a name="see-also"></a>Vea también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
