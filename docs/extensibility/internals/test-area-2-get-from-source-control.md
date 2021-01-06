---
title: 'Área de prueba 2: obtener del control de código fuente | Microsoft Docs'
description: Este área de prueba cubre los casos de prueba para recuperar elementos del almacén de versiones con get. Estos casos de prueba se pueden aplicar tanto a proyectos web como locales.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98ed765f78a9e7330e5e1d3864c8a91b63239a3f
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877707"
---
# <a name="test-area-2-get-from-source-control"></a>Área de prueba 2: Obtención desde el control de código fuente
Este área de prueba cubre los casos de prueba para recuperar elementos del almacén de versiones a través del comando get. Estos casos de prueba se pueden aplicar tanto a proyectos web como locales.

## <a name="command-menu-access"></a>Acceso al menú de comandos
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]En los casos de prueba se usan las siguientes rutas de menú del entorno de desarrollo integrado.

##### <a name="get-latest-version"></a>Obtener la última versión:

- **Archivo**, **control de código fuente**, **obtener la última versión**.

- **Archivo**, **obtener la última versión**.

- Menú contextual, **obtener la última versión**.

- Get: **archivo**, **control de código fuente**, **obtener**.

## <a name="expected-behavior"></a>Comportamiento esperado

##### <a name="get-latest-version"></a>Obtener la última versión:
 Realiza una recuperación silenciosa (sin interfaz de usuario) de la última versión del elemento del almacén de versiones.

##### <a name="get"></a>Get:
 Muestra el cuadro de diálogo **obtener** y permite al usuario realizar cambios en el conjunto de archivos que se recuperarán, así como modificar las opciones que afectan al modo en que se recuperan los archivos.

## <a name="test-cases"></a>Casos de prueba

|Acción|Pasos de prueba|Resultados esperados que se van a comprobar|
|------------|----------------|--------------------------------|
|Obtener la versión más reciente de un archivo que no existe localmente|1. cree un proyecto.<br />2. agregar un elemento al proyecto.<br />3. Coloque el proyecto bajo control de código fuente.<br />4. eliminar la copia local del elemento.<br />5. obtener la versión más reciente del elemento (menú contextual, **obtener la última versión**).|El archivo de elementos se recupera localmente.|
|Obtener un archivo que no existe localmente|1. cree un proyecto.<br />2. agregar un elemento al proyecto.<br />3. Coloque el proyecto bajo control de código fuente.<br />4. eliminar la copia local del elemento.<br />5. obtener el elemento (**archivo**, **control de código fuente**, **obtener** \<item> ).|El archivo de elementos se recupera localmente.|
|Obtener un archivo que se ha desprotegido de forma exclusiva y modificado localmente|1. cree un proyecto.<br />2. agregar un elemento al proyecto.<br />3. Coloque el proyecto bajo control de código fuente.<br />4. Desproteja el elemento de proyecto exclusivamente.<br />5. modifique la copia local.<br />6. obtener la versión más reciente del elemento (**archivo**, **obtener la última versión de** \<item> ). Si este paso se realiza correctamente, continúe con el paso siguiente.<br />7. Haga clic en el botón **reemplazar** en el cuadro de diálogo de advertencia.|**Reresultado del paso 6**`:`<br /><br /> Cuadro de diálogo de advertencia indica que el archivo está desprotegido.<br /><br /> **Reresultado del paso 7:**<br /><br /> El archivo local modificado se sustituye por la versión original del almacén de versiones.<br /><br /> El archivo es de lectura/escritura.|
|Obtener y reemplazar archivos desprotegidos, compartidos y modificados localmente|1. cree un nuevo proyecto.<br />2. agregar un elemento al proyecto.<br />3. Coloque el proyecto bajo control de código fuente.<br />4. Desproteja el elemento de proyecto como compartido.<br />5. modifique la copia local.<br />6. obtener la versión más reciente del elemento (**archivo**, **obtener la última versión de** \<item> ). Si este paso se realiza correctamente, continúe con el paso siguiente.<br />7. Haga clic en **reemplazar** en el cuadro de diálogo de advertencia.|**Resultado del paso 6:**<br /><br /> Cuadro de diálogo de advertencia indica que el archivo está desprotegido.<br /><br /> **Resultado del paso 7:**<br /><br /> El archivo local modificado se sustituye por la versión original del almacén de versiones.<br /><br /> El archivo es de lectura/escritura.|
|Obtener un archivo que existe de forma local, igual que la última versión del almacén de versiones|1. cree un nuevo proyecto.<br />2. agregar un elemento al proyecto.<br />3. Coloque el proyecto bajo control de código fuente.<br />4. obtener el elemento (**archivo**, **control de código fuente**, **obtener** \<item> ).|El archivo local no ha cambiado.|
|Obtener una solución con un proyecto|1. cree una solución con un proyecto.<br />2. Coloque la solución bajo control de código fuente.<br />3. Elimine todos los archivos de proyecto localmente.<br />4. obtener la solución (**archivo**, **control de código fuente**, **obtener**).|Todos los archivos eliminados se restauran localmente.|

## <a name="see-also"></a>Consulte también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
