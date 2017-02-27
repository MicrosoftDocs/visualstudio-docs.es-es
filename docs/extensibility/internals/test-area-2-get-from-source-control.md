---
title: "&#193;rea de prueba 2: Obtener de Control de c&#243;digo fuente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "los complementos, obtener elementos de control de código fuente del control de código fuente"
  - "control de código fuente [Visual Studio SDK], obtener los elementos de"
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# &#193;rea de prueba 2: Obtener de Control de c&#243;digo fuente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta área de ensayo cubre los casos de prueba para recuperar los elementos del almacén de versiones a través del comando Get. Estos casos de prueba se puede aplicar a ambos local y a los proyectos Web.  
  
## Acceso al menú de comandos  
 La siguiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rutas de menú del entorno de desarrollo integrado se utilizan en los casos de prueba.  
  
##### Obtener la versión más reciente:  
  
-   **Archivo**, **Control de código fuente**, **Obtener última versión**.  
  
-   **Archivo**, **Obtener última versión**.  
  
-   Menú contextual, **Obtener última versión**.  
  
-   Get: **archivo**, **Control de código fuente**, **obtener**.  
  
## Comportamiento esperado  
  
##### Obtener la versión más reciente:  
 Realiza una recuperación silenciosa \(sin interfaz de usuario\) de la última versión del elemento desde el almacén de versiones.  
  
##### Get:  
 Muestra el **obtener** cuadro de diálogo y permite al usuario realizar cambios en el conjunto de archivos que se va a recuperar, así como para modificar las opciones que afectan a cómo se recuperan los archivos.  
  
## Casos de prueba  
  
|Acción|Pasos de prueba|Resultados esperados para comprobar|  
|------------|---------------------|-----------------------------------------|  
|Obtener la versión más reciente de un archivo que no existe localmente|1.  Cree un proyecto.<br />2.  Agregar un elemento al proyecto.<br />3.  Coloque el proyecto bajo control de código fuente.<br />4.  Elimine la copia local del elemento.<br />5.  Obtener la última versión del elemento \(menú contextual, **Obtener última versión**\).|Archivo de elemento se recupera localmente.|  
|Obtener un archivo que no existe localmente|1.  Cree un proyecto.<br />2.  Agregar un elemento al proyecto.<br />3.  Coloque el proyecto bajo control de código fuente.<br />4.  Elimine la copia local del elemento.<br />5.  Obtener el elemento \(**archivo**, **Control de código fuente**, **obtener** \< elemento \>\).|Archivo de elemento se recupera localmente.|  
|Obtener un archivo que se ha desprotegido de forma exclusiva y modificado localmente|1.  Cree un proyecto.<br />2.  Agregar un elemento al proyecto.<br />3.  Coloque el proyecto bajo control de código fuente.<br />4.  Desprotege el elemento de proyecto en modo exclusivo.<br />5.  Modificar la copia local.<br />6.  Obtener la última versión del elemento \(**archivo**, **obtener la versión más reciente de** \< elemento \>\). Si este paso se realiza correctamente, vaya al paso siguiente.<br />7.  Haga clic en **reemplazar** botón en el cuadro de diálogo de advertencia.|**ReResult en el paso 6** `:`<br /><br /> Cuadro de diálogo de advertencia indica que ese archivo se desprotege.<br /><br /> **ReResult del paso 7:**<br /><br /> Modificación de archivo local se reemplaza por la versión original del almacén de versiones.<br /><br /> Archivo es de lectura y escritura.|  
|Obtener y reemplazar el archivo que está desprotegido, compartido y modificar localmente|1.  Cree un nuevo proyecto.<br />2.  Agregar un elemento al proyecto.<br />3.  Coloque el proyecto bajo control de código fuente.<br />4.  Desproteger el elemento de proyecto como compartida.<br />5.  Modificar la copia local.<br />6.  Obtener la última versión del elemento \(**archivo**, **obtener la versión más reciente de** \< elemento \>\). Si este paso se realiza correctamente, vaya al paso siguiente.<br />7.  Haga clic en **reemplazar** en el cuadro de diálogo de advertencia.|**Como resultado del paso 6:**<br /><br /> Cuadro de diálogo de advertencia indica que ese archivo se desprotege.<br /><br /> **Como resultado del paso 7:**<br /><br /> Modificación de archivo local se reemplaza por la versión original del almacén de versiones.<br /><br /> Archivo es de lectura y escritura.|  
|Obtener un archivo que existe localmente, igual que la versión más reciente en el almacén de versiones|1.  Cree un nuevo proyecto.<br />2.  Agregar un elemento al proyecto.<br />3.  Coloque el proyecto bajo control de código fuente.<br />4.  Obtener el elemento \(**archivo**, **Control de código fuente**, **obtener** \< elemento \>\).|No se modifica el archivo local.|  
|Obtenga una solución con un proyecto|1.  Crear una solución con un proyecto.<br />2.  Coloque la solución bajo control de código fuente.<br />3.  Eliminar localmente todos los archivos del proyecto.<br />4.  Obtención de la solución \(**archivo**, **Control de código fuente**, **obtener**\).|Todos los archivos eliminados se restauran localmente.|  
  
## Vea también  
 [Guía de pruebas para los complementos de Control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)