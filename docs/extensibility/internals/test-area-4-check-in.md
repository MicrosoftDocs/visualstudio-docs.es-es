---
title: 'Zona de prueba 4: Registrarse ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2386a217de228c5c47b467e6e083d978702927f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704571"
---
# <a name="test-area-4-check-in"></a>Área de prueba 4: insertar en el repositorio
Este área de prueba del complemento de control de código fuente cubre el envío de elementos actualizados al almacén de versiones mediante el comando **Registrar.**

## <a name="command-menu-access"></a>Acceso al menú de comandos
 Las [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] siguientes rutas de menú del entorno de desarrollo integrado se utilizan en los casos de prueba.

##### <a name="check-in"></a>Registrar:
 **Archivo**, **Control de código fuente**, **Registrar**.

 **Archivo**, **Registrar**.

 Menú contextual, **Registrar**.

## <a name="common-expected-behavior"></a>Comportamiento esperado común

- Los proyectos y archivos agregados a una solución o proyecto bajo control de código fuente aparecen en el cuadro de diálogo **Registrar** y en la ventana **Checkins pendientes.**

- Después de la protección, los elementos agregados aparecen en el control de código fuente.

- Después del check-in, los elementos actualizados se versionan correctamente en la tienda.

## <a name="test-cases"></a>Casos de prueba
 Los siguientes son casos de prueba específicos para el área de prueba de check-in.

### <a name="case-4a-modified-items"></a>Caso 4a: Artículos modificados
 Describe el uso de la acción de protección para actualizar un archivo bajo control de código fuente que se ha modificado.

|Acción|Pasos de prueba|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Modificar un archivo de texto que se ha desprotegido, proteger solo el archivo (cuadro de diálogo**Registrar)**|1. Cree un nuevo proyecto con un archivo de texto.<br />2. Agregue la solución al control de código fuente.<br />3. Desproteger y modificar el archivo de texto.<br />4. Regístrese a través del cuadro de diálogo Registrar (**Archivo**, **Control de código fuente**, **Registrar**).|Comportamiento esperado común.|
|Modificar un archivo de texto que se ha desprotegido, Registrar solo archivo (ventana**Checkins pendientes)**|1. Cree un nuevo proyecto con un archivo de texto.<br />2. Agregue la solución al control de código fuente.<br />3. Desproteger y modificar el archivo de texto.<br />4. Regístrese a través de la ventana **Checkins pendientes.**|Comportamiento esperado común.|

### <a name="case-4b-adding-files"></a>Caso 4b: Adición de archivos
 Al agregar un archivo a un proyecto o un elemento a una solución, el proyecto o la solución también debe cambiar. Por lo tanto, el archivo principal también se desprotege y debe protegerse para completar la adición.

|Acción|Pasos de prueba|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Agregar un archivo de texto y registrar todo (cuadro de diálogo**Registrar)**|1. Cree un nuevo proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Agregue un archivo de texto al proyecto.<br />4. Acepte la salida del proyecto si se le solicita.<br />5. Seleccione la solución en el Explorador de **soluciones**.<br />6. Regístrese desde el cuadro de diálogo **Registrar.**|Comportamiento esperado común.|
|Añadir un archivo de texto y registrar todo (ventana**Checkins pendientes)**|1. Cree un nuevo proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Agregue un archivo de texto al proyecto.<br />4. Acepte la salida del proyecto si se le solicita.<br />5. Compruebe la solución desde la ventana **Checkins pendientes.**|Comportamiento esperado común|

### <a name="case-4c-adding-projects"></a>Caso 4c: Adición de proyectos
 Al agregar un proyecto a una solución, la solución también debe cambiar. Por lo tanto, el archivo de solución también se desprotege y debe protegerse para completar la adición.

|Acción|Pasos de prueba|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Agregar un proyecto a una solución en blanco bajo control de código fuente (cuadro de diálogo**Registrar)**|1. Cree una solución en blanco.<br />2. Agregue la solución al control de código fuente.<br />3. Agregue un nuevo proyecto.<br />4. Acepte la salida de la solución si se le solicita.<br />5. Regístrese desde el cuadro de diálogo **Registrar.**|Comportamiento esperado común.|
|Agregar un proyecto a una solución en blanco bajo control de código fuente (ventana**Checkins pendientes)**|1. Cree una solución en blanco.<br />2. Agregue la solución al control de código fuente.<br />3. Agregue un nuevo proyecto.<br />4. Acepte la salida de la solución si se le solicita.<br />5. Compruebe la solución desde la ventana **Checkins pendientes.**|Comportamiento esperado común.|

## <a name="see-also"></a>Vea también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
