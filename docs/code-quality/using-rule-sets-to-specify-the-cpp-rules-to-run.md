---
title: "Usar conjuntos de reglas para especificar las reglas C++ que se van a ejecutar | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Usar conjuntos de reglas para especificar las reglas C++ que se van a ejecutar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] y [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] puede crear y modificar un *conjunto de reglas* personalizado para satisfacer las necesidades concretas del proyecto asociadas a análisis de código.  Para crear un conjunto de reglas personalizadas de C\+\+, un proyecto de C\/C \+\+ debe estar abierto en el IDE de Visual Studio.  Después, abra un conjunto de reglas estándar en el editor de conjuntos de reglas y agregue o quite reglas concretas y cambie opcionalmente la acción que se produce cuando el análisis de código determina que se ha infringido una regla.  
  
 Para crear un nuevo conjunto de reglas personalizado, guárdelo con un nuevo nombre de archivo.  El conjunto de reglas personalizado se asigna automáticamente al proyecto.  
  
## Abrir el editor de conjuntos de reglas  
  
#### Para crear una regla personalizada a partir de un solo conjunto de reglas existente  
  
1.  En el Explorador de soluciones, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
2.  En la pestaña **Propiedades**, elija **Análisis de código**.  
  
3.  En la lista desplegable **Conjunto de reglas**, realice una de las acciones siguientes:  
  
    -   Elija el conjunto de reglas que desee personalizar.  
  
     – O bien –  
  
    -   Elija **\<Examinar...\>** para especificar un conjunto de reglas existente que no esté en la lista.  
  
4.  Elija **Abrir** para mostrar las reglas en el editor de conjuntos de reglas.  
  
#### Para modificar un conjunto de reglas en el editor de conjuntos de reglas  
  
-   Para cambiar el nombre para mostrar del conjunto de reglas, en el menú **Ver**, elija **Ventana de propiedades**.  En el cuadro **Nombre**, escriba el nombre para mostrar.  Observe que el nombre para mostrar puede diferir del nombre de archivo.  
  
-   Para agregar todas las reglas del grupo a un conjunto de reglas personalizado, active la casilla del grupo.  Para quitar todas las reglas del grupo, desactive la casilla.  
  
-   Para agregar una regla concreta al conjunto de reglas personalizado, active la casilla de la regla.  Para quitar la regla del conjunto de reglas, desactive la casilla.  
  
-   Para cambiar la acción que se realiza cuando una regla se infringe en un análisis de código, elija el campo **Acción** de la regla y, a continuación, elija uno de los siguientes valores:  
  
     **Warn**: genera una advertencia.  
  
     **Error**: genera un error.  
  
     **None**: deshabilita la regla.  Esta acción es igual que quitar la regla del conjunto de reglas.  
  
#### Para agrupar, filtrar o cambiar los campos del editor de conjuntos de reglas mediante la barra de herramientas del editor  
  
-   Para expandir las reglas de todos los grupos, elija **Expandir todo**.  
  
-   Para contraer las reglas de todos los grupos, elija **Contraer todo**.  
  
-   Para cambiar el campo por el que se agrupan las reglas, elija el campo en la lista **Agrupar por**.  Para mostrar las reglas desagrupado, elija **\<Ninguno\>**.  
  
-   Para agregar o quitar campos de las columnas de las reglas, elija **Opciones de columna**.  
  
-   Para ocultar reglas que no se aplican a la solución actual, elija **Ocultar reglas que no se aplican a la solución actual**.  
  
-   Para alternar entre mostrar y ocultar reglas que tienen asignada la acción de error, elija **Mostrar reglas que pueden generar errores de análisis de código**.  
  
-   Para alternar entre mostrar y ocultar reglas que tienen asignada la acción de advertencia, elija **Mostrar reglas que pueden generar advertencias de análisis de código**.  
  
-   Para alternar entre mostrar y ocultar las reglas que tienen asignada la acción **Ninguno**, elija **Mostrar reglas no habilitadas**.  
  
-   Para agregar o quitar conjuntos de reglas predeterminadas de Microsoft en el conjunto de reglas actual, elija **Agregar o quitar conjuntos de reglas secundarias**.