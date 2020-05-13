---
title: 'Zona de prueba 3: Desproteger deshaga de salida y deshaga el checkout de salida de salida . Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5365da1e342df5aea9c1b1cd2ae5a446baea57f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704617"
---
# <a name="test-area-3-check-outundo-checkout"></a>Zona de prueba 3: Desproteger/Deshacer pago
Este área de prueba del complemento de control de código fuente cubre la edición y la reversión de elementos del almacén de versiones a través de los comandos **Desproteger** y **Deshacer desprotección.**

**Desproteger**: Marca un elemento en el almacén de versiones como desprotegido, modifica la copia local para leer/escribir.

**Deshacer desprotección**: Marca un elemento en el almacén de versiones como protegido, revierte la copia local al estado antes de la desprotección (dependiendo de las opciones).

## <a name="command-menu-access"></a>Acceso al menú de comandos

Las [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] siguientes rutas de menú del entorno de desarrollo integrado se utilizan en los casos de prueba.

##### <a name="check-out"></a>Modificar:

- **Archivo**, **Control de código fuente**, **Desproteger**.

- **Archivo**, **Desproteger**.

- Menú contextual, **desproteger**.

- Deshacer desprotección: **Archivo**, **Control de código fuente**, Deshacer **desprotección**.

## <a name="common-expected-behavior"></a>Comportamiento esperado común

- Después de la operación de desprotección, los archivos de destino y/o carpetas se marcan como desprotegidos en el almacén de versiones.

- El almacén de versiones atribuye la desprotección al usuario correcto.

- La hora y la fecha de la compra son correctas (según la configuración del usuario).

## <a name="test-cases"></a>Casos de prueba

Los siguientes son casos de prueba específicos para el área de prueba de pago/deshacer pago.

### <a name="case-3a-check-out"></a>Caso 3a: Salida

Esta sección se centra en el funcionamiento del comando check-out.

|Acción|Pasos de prueba|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Echa un vistazo a Exclusive (COE) un proyecto de cliente|1. Cree un proyecto de cliente.<br />2. Agregue la solución al control de código fuente.<br />3. Echa un vistazo a todo el proyecto exclusivamente (**Archivo**, **Desproteger**).|Se produce la salida.|
|Desproteger exclusivo (COE) un sistema de archivos o un proyecto web IIS local|1. Establezca Conexión del servidor web en Compartir archivos en **Herramientas**, **Opciones**, **Proyectos**, **Configuración web**.<br />2. Cree un proyecto Web.<br />3. Agregue la solución al control de código fuente.<br />4. Echa un vistazo a todo el proyecto exclusivamente (**Archivo**, **Control de código fuente**, **Desproteger**).|Se produce la salida.|
|Desproteger elementos de solución en una solución (nuevo método para controlar otros archivos)|1. Cree una solución en blanco.<br />2. Agregue la solución al control de código fuente.<br />3. Compruebe la solución.<br />4. Agregue varios elementos de solución.<br />5. Registre todos los elementos recién agregados.<br />6. Seleccione varios elementos de solución.<br />7. Echa un vistazo a los elementos seleccionados (Menú contextual, **Desproteger**).|Los archivos seleccionados se desprotegen.|
|Desproteger la versión local (si el plug-in bajo prueba admite esta característica)|1. Usuario 1: Crear un proyecto de cliente.<br />2. Usuario 1: Agregue la solución al control de código fuente.<br />3. Usuario 2: Abra la solución desde el control de código fuente a otra ubicación.<br />4. Usuario 2: Echa un vistazo a un archivo.<br />5. Usuario 2: Modifique el archivo.<br />6. Usuario 2: Registre el archivo.<br />7. Usuario 1: Desproteger la versión local del archivo (Desproteger **versión local** avanzada opción en **Desproteger** cuadro de diálogo).|La versión local del archivo está desprotegida.<br /><br /> Las modificaciones del usuario 2 no se aplican al archivo de usuario 1.|

### <a name="case-3b-disconnected-check-out"></a>Caso 3b: Desconexión Desprotección

Operar en modo desconectado permite a los usuarios algún nivel de compatibilidad continua con el control de código fuente cuando no están conectados directamente a un almacén de versiones. Esto se hace almacenando localmente en caché toda la información relevante sobre la solución y los proyectos dados de alta.

Las operaciones exclusivas de desprotección solo pueden producirse mientras están conectados al almacén de control de código fuente. Las operaciones de desprotección compartidas pueden producirse en cualquier momento, ya sea conectadas o desconectadas. Por lo tanto, cuando se desconecta del almacén de versiones, solo se habilita el comando **Desproteger compartido** (COS). Mientras está desconectado, **Deshacer desprotección** está deshabilitado porque la versión anterior no se puede recuperar para reemplazar los cambios realizados por el usuario.

Cuando el usuario se vuelve a conectar al almacén de versiones, se sincronizan los estados de desprotección de todas las soluciones y proyectos dados de alta. Esto hace las actualizaciones necesarias en el almacén para las desprotecciones que el usuario ha realizado. Una vez que se ha producido la sincronización, el usuario puede seguir trabajando de forma normal (conectado).

#### <a name="expected-behavior"></a>Comportamiento esperado

- No se puede utilizar el comando **Desproteger exclusivamente** mientras está desconectado del almacén de versiones.

- No se puede utilizar el comando **Deshacer desprotección** mientras está desconectado del almacén de versiones.

- El comando **Desproteger compartido** funciona.

|Acción|Pasos de prueba|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Mientras está desconectado, desprotege un archivo y, a continuación, conéctate para sincronizar|1. Desconecte un proyecto controlado mediante el cuadro de diálogo Cambiar control de código fuente (**Archivo**, **Control de código fuente**, Cambiar control de código **fuente**).<br />2. Revise un archivo.<br />3. Hacer clic Desproteger (desconectado) en el cuadro de diálogo de advertencia.<br />4. Edite el archivo.<br />5. Conéctese mediante el cuadro de diálogo Cambiar control de código fuente.<br />6. Obtenga la última versión del archivo editado.|Comportamiento esperado común|

### <a name="case-3c-query-editquery-save-qeqs"></a>Caso 3c: Edición de consultas/guardado de consultas (QEQS)
 Se realiza un seguimiento de los elementos bajo control de código fuente para editarlos, cambiar los cambios y guardarlos para ayudar a los usuarios a administrar fácilmente sus archivos. Cuando se edita un elemento controlado que está "protegido", QEQS intercepta el intento de edición y pregunta al usuario si desea desproteger el archivo para editarlo. Dependiendo de **las herramientas**, **configuración** de opciones, el usuario se ve obligado a desproteger el archivo con el fin de editar o se le puede permitir editar una copia en la memoria y desproteger más tarde. Si la configuración **Herramientas**, **Opciones** del usuario no está configurada para mostrar el cuadro de diálogo de desprotección y simplemente desprotegerlo, a continuación, a medida que el usuario realiza su edición, el archivo se desprotege automáticamente, siempre que sea posible.

#### <a name="expected-behavior"></a>Comportamiento esperado

- Después de la operación de desprotección, los archivos de destino y/o carpetas se marcan como desprotegidos en el almacén de versiones.

- El almacén de versiones atribuye la desprotección al usuario correcto.

- La hora y la fecha de la salida son correctas (según la configuración del usuario).

- La copia local del archivo o carpeta de destino se puede escribir.

|Acción|Pasos de prueba|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Editar archivo de texto que está protegido|1. Cree un nuevo proyecto que contenga un archivo de texto.<br />2. Agregue la solución al control de código fuente.<br />3. Establezca **Herramientas**, **Opciones**, **Control de código fuente**, Permitir que los archivos se **editen mientras se desmarca el disco.**<br />4. Establecer **herramientas**, **Opciones**, **Control de código fuente**, Solicitar **desprotección** en el **cuando los archivos marcados se editan** cuadro combinado.<br />5. Establecer **herramientas**, **Opciones**, **Control de código fuente**, Solicitar **desprotección** en el **cuando los archivos marcados se guardan** cuadro combinado.<br />6. Abra el archivo de texto en el editor, intente escribir texto nuevo en el archivo. Si este paso se realiza correctamente, continúe con el paso siguiente.<br />7. Haga clic en **Cancelar** en el cuadro de diálogo **Desproteger para editar.** Si este paso se realiza correctamente, continúe con el paso siguiente.<br />8. Establezca **Herramientas**, **Opciones**, **Control de código fuente**, Permitir que los archivos se **editen mientras se** marca el disco de solo lectura.<br />9. Abra el archivo de proyecto en el editor, intente escribir texto nuevo en el archivo. Si este paso se realiza correctamente, continúe con el paso siguiente.<br />10. Haga clic en **Editar** en el cuadro de diálogo **Desproteger para editar.** Si este paso se realiza correctamente, continúe con el paso siguiente.<br />11. Edite el archivo de texto e intente guardarlo.|`Result of step 6:`<br /><br /> Aparece el cuadro de diálogo Editar para Editar.<br /><br /> `Result of step 7:`<br /><br /> El archivo no ha cambiado.<br /><br /> `Result of step 9:`<br /><br /> Aparece el cuadro de diálogo Editar para Editar.<br /><br /> `Result of step 10:`<br /><br /> Puede editar el archivo de proyecto en la memoria.<br /><br /> `Result of step 11:`<br /><br /> Al guardar, aparece el cuadro de diálogo Desproteger al guardar.|
|Edite un archivo de solución que esté protegido|Repita los pasos descritos en la prueba anterior, pero en lugar de modificar un archivo de texto, modifique la solución cambiando las propiedades de la solución.|Igual que la prueba anterior|
|Editar un archivo de proyecto que está protegido|Repita los pasos descritos en la prueba anterior, pero en lugar de modificar un archivo de texto, modifique el proyecto cambiando las propiedades del proyecto.|Igual que la prueba anterior.|

### <a name="case-3d-silent-check-out"></a>Caso 3d: Silent Check Out
 Esta subárea cubre los escenarios de desprotección en los que el cuadro de diálogo **Desproteger** no aparece por **usuario Herramientas**, **Opciones**, Configuración de Control de **código fuente**.

#### <a name="expected-behavior"></a>Comportamiento esperado

- Después de la operación de desprotección, los archivos de destino y/o carpetas se marcan como desprotegidos en el almacén de versiones.

- El almacén de versiones atribuye la desprotección al usuario correcto.

- La hora y la fecha de la salida es correcta (según la configuración del usuario).

- La copia local del archivo o carpeta de destino se puede escribir.

|Acción|Pasos de prueba|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Pago silencioso para un archivo|1. Establezca **Herramientas**, **Opciones**, **Control de código fuente** en archivos de **desprotección automáticamente al editar**.<br />2. Cree un nuevo proyecto con un archivo.<br />3. Agregue la solución al control de código fuente.<br />4. Echa un vistazo al archivo.|El archivo se desprotege en silencio (sin interfaz de usuario).|
|Pago silencioso para un proyecto|1. Establezca **Herramientas**, **Opciones**, **Control de código fuente** en archivos de **desprotección automáticamente al editar**.<br />2. Cree un nuevo proyecto.<br />3. Agregue la solución al control de código fuente.<br />4. Echa un vistazo al proyecto.|El archivo se desprotege en silencio (sin interfaz de usuario).|

### <a name="case-3e-undo-check-out"></a>Caso 3e: Deshacer desprotección
 **Deshacer desprotección** se utiliza para cancelar el estado de desprotección de un archivo y evitar la comprobación de los cambios realizados en el archivo.

#### <a name="expected-behavior"></a>Comportamiento esperado

- El valor predeterminado se basa en la configuración de la versión local de **desprotección** del usuario. Si el usuario ha elegido desproteger la versión local, el valor predeterminado para deshacer la desprotección es volver siempre a la versión desprotegida.

- Tras la aceptación de la opción deshacer, los iconos del **Explorador** de soluciones se actualizan para los archivos afectados y el elemento se quita de la ventana **Registros pendientes.**

|Acción|Pasos de prueba|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Deshacer desprotección de un único archivo que está desprotegido exclusivamente|1. Cree un proyecto de cliente.<br />2. Agregue la solución al control de código fuente.<br />3. Echa un vistazo a un archivo exclusivamente.<br />4. Modifique el archivo.<br />5. Deshacer desprotección (**Archivo**, **Control de código fuente**, Deshacer **desprotección**).|Comportamiento esperado común.|
|Deshacer desprotección de un único archivo que está desprotegido Compartido|1. Cree un proyecto de cliente.<br />2. Agregue la solución al control de código fuente.<br />3. Echa un vistazo a un archivo compartido.<br />4. Modifique el archivo.<br />5. Deshacer desprotección (**Archivo**, **Control de código fuente**, Deshacer **desprotección**).|Comportamiento esperado común.|
|Deshacer desprotección de un proyecto después de agregar archivos al proyecto|1. Cree un nuevo proyecto y agréguelo al control de código fuente.<br />2. Echa un vistazo al proyecto.<br />3. Agregue un archivo al proyecto.<br />4. Deshacer la compra del proyecto.|El archivo agregado se quita del proyecto en el Explorador de soluciones.<br /><br /> El proyecto ya no se desprotege.|
|Deshacer desprotección de un proyecto después de eliminar archivos del proyecto|1. Cree un nuevo proyecto y agréguelo al control de código fuente.<br />2. Echa un vistazo al proyecto.<br />3. Elimine un archivo del proyecto.<br />4. Deshacer la compra del proyecto.|El archivo eliminado aparece en el proyecto en el Explorador de soluciones.<br /><br /> El proyecto ya no se desprotege.|

## <a name="see-also"></a>Vea también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
