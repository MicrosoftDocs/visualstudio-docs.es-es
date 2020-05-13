---
title: 'Zona de prueba 2: Obtener desde el control de código fuente ? Microsoft Docs'
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
ms.openlocfilehash: c213e2774730596db8b8e4f2d0691472495222e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704599"
---
# <a name="test-area-2-get-from-source-control"></a>Área de prueba 2: obtener de control de código fuente
Esta área de prueba cubre los casos de prueba para recuperar elementos del almacén de versiones mediante el comando Obtener. Estos casos de prueba se pueden aplicar tanto a proyectos locales como a proyectos web.

## <a name="command-menu-access"></a>Acceso al menú de comandos
 Las [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] siguientes rutas de menú del entorno de desarrollo integrado se utilizan en los casos de prueba.

##### <a name="get-latest-version"></a>Obtener la última versión:

- **Archivo**, **Control de código fuente**, Obtener la **versión más reciente**.

- **Archivo**, **Obtener la última versión**.

- Menú contextual, **Obtener la última versión**.

- Obtener: **Archivo**, **Control de código fuente**, **Obtener**.

## <a name="expected-behavior"></a>Comportamiento esperado

##### <a name="get-latest-version"></a>Obtener la última versión:
 Realiza una recuperación silenciosa (sin interfaz de usuario) de la versión más reciente del elemento desde el almacén de versiones.

##### <a name="get"></a>Get:
 Muestra el cuadro de diálogo **Obtener** y permite al usuario realizar cambios en el conjunto de archivos que se recuperarán, así como modificar las opciones que afectan a cómo se recuperan los archivos.

## <a name="test-cases"></a>Casos de prueba

|Acción|Pasos de prueba|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Obtener la última versión de un archivo que NO existe localmente|1. Cree un proyecto.<br />2. Agregue un elemento al proyecto.<br />3. Ponga el proyecto bajo control de código fuente.<br />4. Elimine la copia local del elemento.<br />5. Obtener la última versión del elemento (menú contextual, **obtener la última versión**).|El archivo de elemento se recupera localmente.|
|Obtener un archivo que NO existe localmente|1. Cree un proyecto.<br />2. Agregue un elemento al proyecto.<br />3. Ponga el proyecto bajo control de código fuente.<br />4. Elimine la copia local del elemento.<br />5. Obtenga el elemento **(Archivo**, **Control de código fuente**, **Obtener** \<elemento>).|El archivo de elemento se recupera localmente.|
|Obtener un archivo que ha sido desprotegido exclusivamente y modificado localmente|1. Cree un proyecto.<br />2. Agregue un elemento al proyecto.<br />3. Ponga el proyecto bajo control de código fuente.<br />4. Echa un vistazo al elemento del proyecto exclusivamente.<br />5. Modifique la copia local.<br />6. Obtener la última versión del elemento (**Archivo**, **Obtener la última versión del** \<elemento>). Si este paso se realiza correctamente, continúe con el paso siguiente.<br />7. Hacer clic **Reemplazar** botón en el cuadro de diálogo de advertencia.|**Resultado del paso 6**`:`<br /><br /> El cuadro de diálogo Advertencia indica que el archivo está desprotegido.<br /><br /> **Resultado del paso 7:**<br /><br /> El archivo local modificado se sustituye por la versión original del almacén de versiones.<br /><br /> El archivo es de lectura/escritura.|
|Obtener y reemplazar el archivo que se desprotege, comparte y modifica localmente|1. Cree un nuevo proyecto.<br />2. Agregue un elemento al proyecto.<br />3. Ponga el proyecto bajo control de código fuente.<br />4. Consulte el elemento del proyecto como compartido.<br />5. Modifique la copia local.<br />6. Obtener la última versión del elemento (**Archivo**, **Obtener la última versión del** \<elemento>). Si este paso se realiza correctamente, continúe con el paso siguiente.<br />7. Haga clic en **Reemplazar** en el cuadro de diálogo de advertencia.|**Resultado del paso 6:**<br /><br /> El cuadro de diálogo Advertencia indica que el archivo está desprotegido.<br /><br /> **Resultado del paso 7:**<br /><br /> El archivo local modificado se sustituye por la versión original del almacén de versiones.<br /><br /> El archivo es de lectura/escritura.|
|Obtener un archivo que exista localmente, igual que la versión más reciente en el almacén de versiones|1. Cree un nuevo proyecto.<br />2. Agregue un elemento al proyecto.<br />3. Ponga el proyecto bajo control de código fuente.<br />4. Obtenga el elemento **(Archivo**, **Control de código fuente**, **Obtener** \<elemento>).|El archivo local no cambia.|
|Obtenga una solución con un proyecto|1. Cree una solución con un proyecto.<br />2. Coloque la solución bajo control de código fuente.<br />3. Elimine todos los archivos de proyecto localmente.<br />4. Obtenga la solución (**File**, **Source Control**, **Get**).|Todos los archivos eliminados se restauran localmente.|

## <a name="see-also"></a>Vea también
- [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
