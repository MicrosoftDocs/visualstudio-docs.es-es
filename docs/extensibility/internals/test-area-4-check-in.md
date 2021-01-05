---
title: 'Área de prueba 4: proteger | Microsoft Docs'
description: Este área de prueba del complemento de control de código fuente cubre el envío de elementos actualizados al almacén de versiones mediante el comando proteger.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ffe0e7838c3bde048df2514c54e534cf7a9b3475
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875234"
---
# <a name="test-area-4-check-in"></a>Área de prueba 4: Inserción en el repositorio
Este área de prueba del complemento de control de código fuente cubre el envío de elementos actualizados al almacén de versiones a través del comando **de inserción en el repositorio** .

## <a name="command-menu-access"></a>Acceso al menú de comandos
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]En los casos de prueba se usan las siguientes rutas de menú del entorno de desarrollo integrado.

##### <a name="check-in"></a>Registrar:
 **Archivo**, **control de código fuente**, **proteger**.

 **Archivo**, **proteger**.

 Menú contextual, **proteger**.

## <a name="common-expected-behavior"></a>Comportamiento esperado común

- Los proyectos y archivos agregados a una solución o proyecto bajo control de código fuente aparecen en el cuadro **de diálogo proteger** y en la ventana **protecciones pendientes** .

- Después de la inserción en el repositorio, los elementos agregados aparecen en el control de código fuente.

- Después de la inserción en el repositorio, los elementos actualizados tienen versiones correctas en el almacén.

## <a name="test-cases"></a>Casos de prueba
 Los siguientes son casos de prueba específicos para el área de prueba de protección.

### <a name="case-4a-modified-items"></a>Caso 4a: Elementos modificados
 Describe el uso de la acción de inserción en el repositorio para actualizar un archivo bajo control de código fuente que se ha modificado.

|Acción|Pasos de prueba|Resultados esperados que se van a comprobar|
|------------|----------------|--------------------------------|
|Modificar un archivo de texto que se ha desprotegido, proteger únicamente el archivo (cuadro de diálogo **proteger** )|1. cree un nuevo proyecto con un archivo de texto.<br />2. Agregue la solución al control de código fuente.<br />3. desproteja y modifique el archivo de texto.<br />4. proteger mediante el cuadro de diálogo proteger (**archivo**, **control de código fuente**, **proteger**).|Comportamiento esperado común.|
|Modificar un archivo de texto que se ha desprotegido, proteger solo el archivo (ventana **protecciones pendientes** )|1. cree un nuevo proyecto con un archivo de texto.<br />2. Agregue la solución al control de código fuente.<br />3. desproteja y modifique el archivo de texto.<br />4. Proteja a través de la ventana **protecciones pendientes** .|Comportamiento esperado común.|

### <a name="case-4b-adding-files"></a>Caso 4b: Adición de archivos
 Al agregar un archivo a un proyecto o un elemento a una solución, el proyecto o la solución también deben cambiar. Por lo tanto, el archivo primario también se desprotege y se debe proteger para completar la adición.

|Acción|Pasos de prueba|Resultados esperados que se van a comprobar|
|------------|----------------|--------------------------------|
|Agregar un archivo de texto y protegerlo todo (cuadro **de diálogo proteger** )|1. cree un nuevo proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Agregue un archivo de texto al proyecto.<br />4. acepte la extracción del proyecto si se le solicita.<br />5. Seleccione la solución en **Explorador de soluciones**.<br />6. Proteja en el cuadro de diálogo **proteger** .|Comportamiento esperado común.|
|Agregar un archivo de texto y protegerlo todo (ventana **protecciones pendientes** )|1. cree un nuevo proyecto.<br />2. Agregue la solución al control de código fuente.<br />3. Agregue un archivo de texto al proyecto.<br />4. acepte la extracción del proyecto si se le solicita.<br />5. Proteja la solución desde la ventana **protecciones pendientes** .|Comportamiento esperado común|

### <a name="case-4c-adding-projects"></a>Caso 4c: Adición de proyectos
 Al agregar un proyecto a una solución, la solución debe cambiar también. Por lo tanto, el archivo de solución también se desprotege y se debe proteger para completar la adición.

|Acción|Pasos de prueba|Resultados esperados que se van a comprobar|
|------------|----------------|--------------------------------|
|Agregar un proyecto a una solución en blanco bajo control de código fuente (cuadro **de diálogo proteger** )|1. cree una solución en blanco.<br />2. Agregue la solución al control de código fuente.<br />3. Agregue un nuevo proyecto.<br />4. acepte la desprotección de la solución si se le solicita.<br />5. Proteja desde el cuadro de diálogo **proteger** .|Comportamiento esperado común.|
|Agregar un proyecto a una solución en blanco en el control de código fuente (ventana **protecciones pendientes** )|1. cree una solución en blanco.<br />2. Agregue la solución al control de código fuente.<br />3. Agregue un nuevo proyecto.<br />4. acepte la desprotección de la solución si se le solicita.<br />5. Proteja la solución desde la ventana **protecciones pendientes** .|Comportamiento esperado común.|

## <a name="see-also"></a>Consulte también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
