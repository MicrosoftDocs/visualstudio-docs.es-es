---
title: "C&#243;mo: Comparar archivos de datos del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vsperf.choosediffbinaries"
helpviewer_keywords: 
  - "archivos de resultados del generador de perfiles, cómo comparar"
  - "herramientas de generación de perfiles, cómo comparar archivos de resultados del generador de perfiles"
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# C&#243;mo: Comparar archivos de datos del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede comparar los resultados de dos archivos de datos diferentes \(.vsp o .vsps\) del generador de perfiles si crea una nueva vista o informe de comparación \("Diff"\).  La comparación muestra las diferencias, reducciones de rendimiento y mejoras producidas en una sesión de generación de perfiles respecto a otra.  
  
 El informe Diff presenta una vista de tabla de los datos.  La tabla presenta el delta o cambio respecto de la línea base.  Esto se calcula determinando la diferencia entre el valor anterior, el valor de línea base y el valor de resultado del nuevo análisis.  
  
 Las comparaciones de datos del generador de perfiles pueden estar basadas en funciones del código, módulos de la aplicación, líneas, punteros de instrucción \(IP\) y tipos.  
  
 Se puede establecer un umbral para reducir el ruido y filtrar cualquier dato que aparezca en la vista de tabla de las filas que no han cambiado en una cantidad especificada.  
  
### Para crear una vista de archivos de comparación para un proyecto en el Explorador de rendimiento  
  
1.  En el **Explorador de rendimiento**, bajo **Informes**, seleccione el archivo de informe .vsp o .vsps que desee utilizar como valores de línea base para la comparación.  
  
2.  Seleccione los archivos de informe .vsp o .vsps que desea comparar.  
  
3.  Haga clic con el botón secundario del mouse en uno de los archivos seleccionados y, a continuación, haga clic en **Comparar informes**.  
  
### Para comparar valores  
  
1.  Seleccione la ficha **Informe de comparación** en la ventana de la vista de informe.  
  
2.  En la lista desplegable **Tabla**, seleccione la función o los módulos que se van a comparar.  
  
3.  En la lista desplegable **Columna**, seleccione el valor que desee comparar.  
  
4.  \(opcional\) Escriba un valor para **Umbral**.  
  
5.  Haga clic en **Aplicar**.  
  
### Para comparar archivos de informe  
  
1.  En el menú **Analizar** , seleccione **Comparar informes de rendimiento**.  
  
2.  En la ventana **Seleccionar archivos de análisis para compararlos**, examine y seleccione los archivos de análisis **Archivo de línea base**  \(.vsp o .vsps\) y **Archivo de comparación** \(.vsp o .vsps\).  
  
3.  Haga clic en **Aceptar**.