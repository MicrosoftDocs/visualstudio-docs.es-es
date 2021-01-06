---
title: 'Área de prueba 3: comprobar Out-Undo desprotección | Microsoft Docs'
description: Este área de prueba del complemento de control de código fuente cubre la edición y reversión de los elementos del almacén de versiones mediante los comandos desproteger y Deshacer desproteger.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b6292051e6ddf11e3ce4b56648574e0207bb5a41
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877694"
---
# <a name="test-area-3-check-outundo-checkout"></a>Área de prueba 3: Extracción del repositorio y cancelación de la operación
Este área de prueba del complemento de control de código fuente cubre la edición y reversión de los elementos del almacén de versiones a través de los comandos **Desproteger** y **Deshacer desproteger** .

**Desproteger: marca** un elemento en el almacén de versiones como desprotegido, modifica la copia local a lectura/escritura.

**Deshacer desprotección**: marca un elemento en el almacén de versiones como protegido, revierte la copia local al estado anterior a la desprotección (dependiendo de las opciones).

## <a name="command-menu-access"></a>Acceso al menú de comandos

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]En los casos de prueba se usan las siguientes rutas de menú del entorno de desarrollo integrado.

##### <a name="check-out"></a>Modificar:

- **Archivo**, **control de código fuente**, **Desproteger**.

- **Archivo**, **Desproteger**.

- Menú contextual, **Desproteger**.

- Deshacer desprotección: **archivo**, **control de código fuente**, **Deshacer desprotección**.

## <a name="common-expected-behavior"></a>Comportamiento esperado común

- Después de la operación de desprotección, los archivos o carpetas de destino se marcan como desprotegidos en el almacén de versiones.

- El almacén de versiones modifica los atributos de la desprotección al usuario correcto.

- La fecha y la hora de la desprotección son correctas (según la configuración del usuario).

## <a name="test-cases"></a>Casos de prueba

Los siguientes son casos de prueba específicos para el área de prueba de desprotección/Deshacer desprotección.

### <a name="case-3a-check-out"></a>Caso 3a: Desproteger

Esta sección se centra en el funcionamiento del comando Desproteger.

|Acción|Pasos de prueba|Resultados esperados que se van a comprobar|
|------------|----------------|--------------------------------|
|Desproteger un proyecto de cliente exclusivo (COE)|1. cree un proyecto de cliente.<br />2. Agregue la solución al control de código fuente.<br />3. desproteja todo el proyecto exclusivamente (**archivo**, **Desproteger**).|Se produce la desprotección.|
|Desproteger en exclusiva (COE) un sistema de archivos o un proyecto Web de IIS local|1. establezca la conexión del servidor Web en el recurso compartido de archivos en **herramientas**, **Opciones**, **proyectos**, **configuración Web**.<br />2. crear un proyecto Web.<br />3. agregar la solución al control de código fuente.<br />4. desproteja todo el proyecto exclusivamente (**archivo**, **control de código fuente**, **Desproteger**).|Se produce la desprotección.|
|Desproteger elementos de la solución en una solución (nuevo método para controlar otros archivos)|1. cree una solución en blanco.<br />2. Agregue la solución al control de código fuente.<br />3. Consulte la solución.<br />4. agregar varios elementos de solución.<br />5. Proteja todos los elementos recién agregados.<br />6. Seleccione varios elementos de la solución.<br />7. desproteger los elementos seleccionados (menú contextual, **Desproteger**).|Los archivos seleccionados están desprotegidos.|
|Desproteger la versión local (si el complemento en pruebas es compatible con esta característica)|1. usuario 1: cree un proyecto de cliente.<br />2. usuario 1: agregar la solución al control de código fuente.<br />3. usuario 2: Abra la solución desde el control de código fuente a otra ubicación.<br />4. usuario 2: desproteger un archivo.<br />5. usuario 2: modifique el archivo.<br />6. usuario 2: Proteja el archivo.<br />7. usuario 1: desproteger la versión local del archivo (Active la opción desproteger la **versión local** en el cuadro de diálogo **Desproteger)** .|La versión local del archivo está desprotegida.<br /><br /> Las modificaciones realizadas por el usuario 2 no se aplican al archivo del usuario 1.|

### <a name="case-3b-disconnected-check-out"></a>Caso 3B: desconexión desconectada

El funcionamiento en modo sin conexión permite a los usuarios cierto nivel de compatibilidad continua de control de código fuente cuando no se adjuntan directamente a un almacén de versiones. Esto se hace almacenando localmente en caché toda la información relevante sobre la solución y los proyectos que se han dado de alta.

Solo se pueden realizar operaciones de desprotección exclusivas mientras están conectadas al almacén de control de código fuente. Las operaciones de desprotección compartidas pueden producirse en cualquier momento, ya sea conectado o desconectado. Por lo tanto, cuando se desconecta del almacén de versiones, solo está habilitado el comando **Desproteger compartido** (COS). Mientras está desconectado, **Deshacer desprotección** está deshabilitado porque no se puede recuperar la versión anterior para reemplazar los cambios realizados por el usuario.

Cuando el usuario se vuelve a conectar al almacén de versiones, se sincronizan los Estados de desprotección de todas las soluciones y proyectos dadas de alta. Esto hace las actualizaciones necesarias en el almacén para las desprotecciones que ha realizado el usuario. Una vez que se ha producido la sincronización, el usuario puede seguir trabajando como normal (conectado).

#### <a name="expected-behavior"></a>Comportamiento esperado

- No se puede usar el comando **Desproteger exclusivamente** mientras está desconectado del almacén de versiones.

- No se puede usar el comando **Deshacer desprotección** mientras está desconectado del almacén de versiones.

- El comando de **desprotección compartida** funciona.

|Acción|Pasos de prueba|Resultados esperados que se van a comprobar|
|------------|----------------|--------------------------------|
|Mientras está desconectado, desproteja un archivo y, a continuación, conéctese a la sincronización|1. desconectar un proyecto controlado mediante el cuadro de diálogo Cambiar control de código fuente (**archivo**, **control de código fuente**, **Cambiar control de código fuente**).<br />2. desproteger un archivo.<br />3. Haga clic en Desproteger (desconectada) en el cuadro de diálogo de advertencia.<br />4. edite el archivo.<br />5. Conéctese mediante el cuadro de diálogo Cambiar control de código fuente.<br />6. obtener la versión más reciente del archivo editado.|Comportamiento esperado común|

### <a name="case-3c-query-editquery-save-qeqs"></a>Caso 3c: Edición o guardado de consultas (QEQS)
 Se realiza un seguimiento de los elementos bajo control de código fuente para editar, cambiar y guardar para ayudar a los usuarios a administrar fácilmente sus archivos. Cuando se edita un elemento controlado que está "protegido", QEQS intercepta el intento de edición y pregunta al usuario si desea desproteger el archivo para editarlo. En función de las **herramientas**, la configuración de **Opciones** , el usuario se ve obligado a desproteger el archivo para editarlo o se le puede permitir editar una copia en la memoria y desprotegerlo más tarde. Si la opción **herramientas** del usuario, **Opciones** no está establecida para mostrar el cuadro de diálogo desproteger y simplemente desprotegerlo, cuando el usuario realice su edición, el archivo se desprotegerá automáticamente, siempre que sea posible.

#### <a name="expected-behavior"></a>Comportamiento esperado

- Después de la operación de desprotección, los archivos o carpetas de destino se marcan como desprotegidos en el almacén de versiones.

- El almacén de versiones marca la desprotección para el usuario correcto.

- La fecha y la hora de la desprotección son correctas (según la configuración del usuario).

- La copia local del archivo o carpeta de destino es grabable.

|Acción|Pasos de prueba|Resultados esperados que se van a comprobar|
|------------|----------------|--------------------------------|
|Editar archivo de texto que está protegido|1. cree un nuevo proyecto que contenga un archivo de texto.<br />2. Agregue la solución al control de código fuente.<br />3. establezca **herramientas**, **Opciones**, **control de código fuente**, **permitir que los archivos se editen mientras se está** desactivando el disco.<br />4. establezca **herramientas**, **Opciones**, **control de código fuente**, **preguntar para desproteger** en el cuadro combinado **cuando se editan archivos** insertados.<br />5. establezca **herramientas**, **Opciones**, **control de código fuente**, **preguntar para desproteger** en el cuadro combinado **cuando se guardan archivos** insertados.<br />6. Abra el archivo de texto en el editor, intente escribir un nuevo texto en el archivo. Si este paso se realiza correctamente, continúe con el paso siguiente.<br />7. Haga clic en **Cancelar** en el cuadro **de diálogo desproteger para editar** . Si este paso se realiza correctamente, continúe con el paso siguiente.<br />8. establezca **herramientas**, **Opciones**, **control de código fuente**, **permitir que los archivos se editen mientras se está en el disco de solo lectura** .<br />9. Abra el archivo de proyecto en el editor, intente escribir un nuevo texto en el archivo. Si este paso se realiza correctamente, continúe con el paso siguiente.<br />10. Haga clic en **Editar** en el cuadro **de diálogo desproteger para editar** . Si este paso se realiza correctamente, continúe con el paso siguiente.<br />11. edite el archivo de texto e intente guardarlo.|`Result of step 6:`<br /><br /> Aparece el cuadro de diálogo desproteger para editar.<br /><br /> `Result of step 7:`<br /><br /> El archivo no ha cambiado.<br /><br /> `Result of step 9:`<br /><br /> Aparece el cuadro de diálogo desproteger para editar.<br /><br /> `Result of step 10:`<br /><br /> Puede editar el archivo de proyecto en memoria.<br /><br /> `Result of step 11:`<br /><br /> Al guardar, aparece el cuadro de diálogo desproteger al guardar.|
|Editar un archivo de solución que está protegido|Repita los pasos descritos en la prueba anterior, pero en lugar de modificar un archivo de texto, modifique la solución cambiando las propiedades de la solución.|Igual que la prueba anterior|
|Editar un archivo de proyecto que está protegido|Repita los pasos descritos en la prueba anterior, pero en lugar de modificar un archivo de texto, modifique Project cambiando las propiedades del proyecto.|Igual que la prueba anterior.|

### <a name="case-3d-silent-check-out"></a>Caso 3D: desprotección silenciosa
 En este tema se **describen los escenarios** de desprotección en los que el cuadro de diálogo desproteger no aparece en las **herramientas**, **Opciones**, configuración de **control de código fuente** del usuario.

#### <a name="expected-behavior"></a>Comportamiento esperado

- Después de la operación de desprotección, los archivos o carpetas de destino se marcan como desprotegidos en el almacén de versiones.

- El almacén de versiones marca la desprotección para el usuario correcto.

- La fecha y la hora de la desprotección son correctas (según la configuración del usuario).

- La copia local del archivo o carpeta de destino es grabable.

|Acción|Pasos de prueba|Resultados esperados que se van a comprobar|
|------------|----------------|--------------------------------|
|Desprotección silenciosa de un archivo|1. establezca **herramientas**, **Opciones**, **control de código fuente** para **Desproteger los archivos automáticamente al editarlos**.<br />2. crear un nuevo proyecto con un archivo.<br />3. agregar la solución al control de código fuente.<br />4. Desproteja el archivo.|El archivo se desprotege de forma silenciosa (sin interfaz de usuario).|
|Desprotección silenciosa para un proyecto|1. establezca **herramientas**, **Opciones**, **control de código fuente** para **Desproteger los archivos automáticamente al editarlos**.<br />2. cree un nuevo proyecto.<br />3. agregar la solución al control de código fuente.<br />4. Desproteja el proyecto.|El archivo se desprotege de forma silenciosa (sin interfaz de usuario).|

### <a name="case-3e-undo-check-out"></a>Caso 3e: Deshacer desprotección
 **Deshacer desprotección** se usa para cancelar el estado desprotegido de un archivo y evitar la protección de los cambios realizados en el archivo.

#### <a name="expected-behavior"></a>Comportamiento esperado

- El valor predeterminado se basa en la configuración de la **versión local de desprotección** del usuario. Si el usuario ha elegido desproteger la versión local, el valor predeterminado para Deshacer desprotección es siempre revertir a la versión desprotegida.

- Tras la aceptación de la operación de deshacer, los iconos de **Explorador de soluciones** se actualizan para los archivos afectados y el elemento se quita de la ventana **protecciones pendientes** .

|Acción|Pasos de prueba|Resultados esperados que se van a comprobar|
|------------|----------------|--------------------------------|
|Deshacer la desprotección de un solo archivo desprotegido exclusivamente|1. cree un proyecto de cliente.<br />2. Agregue la solución al control de código fuente.<br />3. desproteja un archivo exclusivamente.<br />4. modifique el archivo.<br />5. deshacer la desprotección (**archivo**, **control de código fuente**, **Deshacer desprotección**).|Comportamiento esperado común.|
|Deshacer la desprotección de un solo archivo que está desprotegido compartido|1. cree un proyecto de cliente.<br />2. Agregue la solución al control de código fuente.<br />3. desproteja un archivo compartido.<br />4. modifique el archivo.<br />5. deshacer la desprotección (**archivo**, **control de código fuente**, **Deshacer desprotección**).|Comportamiento esperado común.|
|Deshacer la desprotección de un proyecto después de agregar archivos al proyecto|1. cree un nuevo proyecto y agréguelo al control de código fuente.<br />2. Desproteja el proyecto.<br />3. Agregue un archivo al proyecto.<br />4. deshacer la desprotección del proyecto.|El archivo agregado se quita del proyecto en Explorador de soluciones.<br /><br /> El proyecto ya no está desprotegido.|
|Deshacer la desprotección de un proyecto después de eliminar archivos del proyecto|1. cree un nuevo proyecto y agréguelo al control de código fuente.<br />2. Desproteja el proyecto.<br />3. eliminar un archivo del proyecto.<br />4. deshacer la desprotección del proyecto.|El archivo eliminado aparece en el proyecto en Explorador de soluciones.<br /><br /> El proyecto ya no está desprotegido.|

## <a name="see-also"></a>Consulte también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
