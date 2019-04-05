---
title: 'Área de prueba 2: Obtener de Control de código fuente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 78ecbcb50effc133487f03ffd2f2edee3cbd8d4a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995548"
---
# <a name="test-area-2-get-from-source-control"></a>Área de prueba 2: Obtención desde el control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta área de prueba trata los casos de prueba para recuperar los elementos del almacén de versiones mediante el comando Get. Estos casos de prueba se pueden aplicar a ambos local y a los proyectos Web.  
  
## <a name="command-menu-access"></a>Acceso al menú de comandos  
 La siguiente [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rutas de menú del entorno de desarrollo integrado que se usan en los casos de prueba.  
  
##### <a name="get-latest-version"></a>Obtener la versión más reciente:  
  
-   **Archivo**, **Control de código fuente**, **obtener última versión**.  
  
-   **Archivo**, **obtener última versión**.  
  
-   Menú contextual, **obtener última versión**.  
  
-   Obtener: **Archivo**, **Control de código fuente**, **obtener**.  
  
## <a name="expected-behavior"></a>Comportamiento esperado  
  
##### <a name="get-latest-version"></a>Obtener la versión más reciente:  
 Realiza una recuperación silenciosa (sin interfaz de usuario) de la versión más reciente del elemento del almacén de versiones.  
  
##### <a name="get"></a>Obtener:  
 Muestra el **obtener** cuadro de diálogo y permite al usuario realizar cambios en el conjunto de archivos que se va a recuperar, así como para modificar las opciones que afectan a cómo se recuperan los archivos.  
  
## <a name="test-cases"></a>Casos de prueba  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|----------------|--------------------------------|  
|Obtener la versión más reciente de un archivo que no existe localmente|1.  Cree un proyecto.<br />2.  Agregar un elemento al proyecto.<br />3.  Coloque el proyecto bajo control de código fuente.<br />4.  Elimine la copia local del elemento.<br />5.  Obtener la versión más reciente del elemento (menú contextual, **obtener última versión**).|Archivo de elemento se recupera localmente.|  
|Obtener un archivo que no existe localmente|1.  Cree un proyecto.<br />2.  Agregar un elemento al proyecto.<br />3.  Coloque el proyecto bajo control de código fuente.<br />4.  Elimine la copia local del elemento.<br />5.  Obtener el elemento (**archivo**, **Control de código fuente**, **obtener** \<elemento >).|Archivo de elemento se recupera localmente.|  
|Obtener un archivo que se ha desprotegido exclusivamente y modificado localmente|1.  Cree un proyecto.<br />2.  Agregar un elemento al proyecto.<br />3.  Coloque el proyecto bajo control de código fuente.<br />4.  Desprotege el elemento de proyecto en modo exclusivo.<br />5.  Modificar la copia local.<br />6.  Obtener la versión más reciente del elemento (**archivo**, **obtener la versión más reciente de** \<elemento >). Si este paso se realiza correctamente, vaya al paso siguiente.<br />7.  Haga clic en **reemplazar** botón en el cuadro de diálogo de advertencia.|**ReResult del paso 6** `:`<br /><br /> Cuadro de diálogo de advertencia indica que ese archivo está desprotegido.<br /><br /> **ReResult del paso 7:**<br /><br /> Archivo local modificado se reemplaza por la versión original del almacén de versiones.<br /><br /> Archivo es de lectura/escritura.|  
|Obtener y reemplace el archivo que está desprotegido, compartido y modificar localmente|1.  Cree un nuevo proyecto.<br />2.  Agregar un elemento al proyecto.<br />3.  Coloque el proyecto bajo control de código fuente.<br />4.  Consulte el elemento de proyecto como compartido.<br />5.  Modificar la copia local.<br />6.  Obtener la versión más reciente del elemento (**archivo**, **obtener la versión más reciente de** \<elemento >). Si este paso se realiza correctamente, vaya al paso siguiente.<br />7.  Haga clic en **reemplazar** en el cuadro de diálogo de advertencia.|**Como resultado del paso 6:**<br /><br /> Cuadro de diálogo de advertencia indica que ese archivo está desprotegido.<br /><br /> **Como resultado del paso 7:**<br /><br /> Archivo local modificado se reemplaza por la versión original del almacén de versiones.<br /><br /> Archivo es de lectura/escritura.|  
|Obtener un archivo que existe localmente, igual a la versión más reciente en el almacén de versiones|1.  Cree un nuevo proyecto.<br />2.  Agregar un elemento al proyecto.<br />3.  Coloque el proyecto bajo control de código fuente.<br />4.  Obtener el elemento (**archivo**, **Control de código fuente**, **obtener** \<elemento >).|No se modifica el archivo local.|  
|Obtener una solución con un proyecto|1.  Crear una solución con un proyecto.<br />2.  Coloque la solución bajo control de código fuente.<br />3.  Eliminar localmente todos los archivos del proyecto.<br />4.  Obtención de la solución (**archivo**, **Control de código fuente**, **obtener**).|Todos los archivos eliminados se restauran localmente.|  
  
## <a name="see-also"></a>Vea también  
 [Guía de pruebas para los complementos de control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
