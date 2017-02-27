---
title: "Probar &#225;rea 6: eliminar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control de código fuente [Visual Studio SDK], eliminar elementos"
  - "origen control complementos, eliminar elementos"
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Probar &#225;rea 6: eliminar
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cubre del complemento de esta área de prueba de control de código fuente eliminan acciones.  
  
 El control de origen responde a las acciones de eliminación en **Explorador de soluciones**.  
  
 A continuación se muestra una lista de elementos que pueden eliminarse:  
  
-   Files \(Archivos\)  
  
-   Carpetas  
  
-   Proyecto  
  
 Según el tipo de proyecto, podría tener la opción a **Quitar** el proyecto \(permite los archivos en disco\) o **Eliminar** el proyecto \(quita los archivos en el disco\).  Cualquier acción quita el proyecto o elemento de **Explorador de soluciones**.  
  
## El comportamiento esperado  
 El comportamiento esperado para los casos de prueba en el área de probar la cancelación es:  
  
-   El elemento eliminado ya no es visible dentro de **Explorador de soluciones**.  
  
-   El elemento primario del proyecto o elemento eliminado se desprotege según sea necesario \(posiblemente con un indicador\).  
  
-   Después de eliminar desprotegido o el elemento agregado, NOT aparece en la ventana de **Protecciones pendientes** .  
  
-   El elemento todavía existe dentro del almacén de control de código fuente, incluso después de la eliminación, y debe ser purgado manualmente.  
  
|Acción|Pasos de prueba|Resultados esperado a comprobar|  
|------------|---------------------|-------------------------------------|  
|Elimine un proyecto cliente|1.  cree un proyecto de cliente.<br />2.  Agregar la solución al control de código fuente.<br />3.  Quite todo el proyecto de la solución|El comportamiento esperado común.|  
|elimine un archivo vacío|1.  cree un proyecto de cliente.<br />2.  Agregue un archivo de octeto cero al proyecto.<br />3.  Agregar la solución al control de código fuente.<br />4.  Seleccione el archivo, elimínelo.|El comportamiento esperado común.|  
|Eliminar una carpeta con un archivo|1.  Cree la única solución de proyecto.<br />2.  agregue una carpeta.<br />3.  Agregue un archivo en la carpeta.<br />4.  Agregar la solución al control de código fuente.<br />5.  Desproteja el proyecto de evitar los marcadores.<br />6.  elimine la carpeta.|El comportamiento esperado común.|  
|Elimine un proyecto web de sistema de archivos|1.  Cree un proyecto web de sistema de archivos \(utilice el botón examinar para especificar una ruta UNC.<br />2.  Agregar la solución al control de código fuente.<br />3.  Quite todo el proyecto de la solución.<br />4.  Repita los pasos 1 a 3 para un proyecto web local \(diferentes rutas de procedimientos con el código pero tienen la misma interfaz externa y comportamiento\).|El comportamiento esperado común.|  
|Eliminar un archivo de un proyecto web de sistema de archivos|1.  Cree un proyecto web de sistema de archivos.<br />2.  Agregar la solución al control de código fuente.<br />3.  Eliminar un archivo de proyecto.<br />4.  Repita los pasos 1 a 3 para un proyecto web local \(diferentes rutas de procedimientos con el código pero tienen la misma interfaz externa y comportamiento\).|El comportamiento esperado común.|  
  
## Vea también  
 [Guía de pruebas para los complementos de Control de código fuente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)