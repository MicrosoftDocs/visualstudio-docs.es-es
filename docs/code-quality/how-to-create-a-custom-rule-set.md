---
title: "C&#243;mo: Crear un conjunto de reglas personalizadas | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.addremoverulesets"
helpviewer_keywords: 
  - "Development Edition, conjuntos de reglas"
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Crear un conjunto de reglas personalizadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)], [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] y [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)] puede crear y modificar un *conjunto de reglas* personalizado para satisfacer las necesidades concretas del proyecto asociadas al análisis de código.  Para crear un conjunto de reglas personalizado, se abren uno o más conjuntos de reglas estándar en el editor del conjuntos de reglas.  Se pueden agregar o quitar reglas concretas y cambiar la acción que se realiza cuando el análisis de código determina que se ha infringido una regla.  
  
 Para crear un nuevo conjunto de reglas personalizado, guárdelo con un nuevo nombre de archivo.  El conjunto de reglas personalizado se asigna automáticamente al proyecto.  
  
## Abrir el editor de conjuntos de reglas  
  
#### Para abrir un archivo de conjunto de reglas vacío en el editor de conjuntos de reglas  
  
1.  En el menú **Archivo** de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], elija **Nuevo** y, a continuación, haga clic en **Archivo**.  
  
2.  En el cuadro de diálogo **Nuevo archivo**, haga clic en **General** en la lista **Plantillas instaladas** y, a continuación, seleccione **Conjunto de reglas de análisis de código**.  
  
3.  Se abre el editor de conjuntos de reglas.  No hay ninguna regla seleccionada en la lista del editor.  
  
#### Para crear una regla personalizada a partir de un solo conjunto de reglas existente  
  
1.  En el Explorador de soluciones, haga clic con el botón secundario del mouse en el proyecto y, a continuación, seleccione **Propiedades**.  
  
2.  En la pestaña **Propiedades**, haga clic en **Análisis de código**.  
  
3.  En la lista desplegable **Conjunto de reglas**, realice una de las acciones siguientes:  
  
    -   Seleccione el conjunto de reglas que desee personalizar.  
  
     – O bien –  
  
    -   Seleccione **\<Examinar...\>** para especificar un conjunto de reglas existente que no esté en la lista.  
  
4.  Haga clic en **Abrir** para mostrar las reglas en el editor de conjuntos de reglas.  
  
#### Para crear un conjunto de reglas personalizado a partir de varios conjuntos de reglas existentes  
  
1.  En el Explorador de soluciones, haga clic con el botón secundario del mouse en el proyecto y, a continuación, seleccione **Propiedades**.  
  
2.  En la pestaña **Propiedades**, haga clic en **Análisis de código**.  
  
3.  Seleccione **\<Elegir varios conjuntos de reglas...\>** en **Ejecutar este conjunto de reglas**.  
  
4.  En el cuadro de diálogo **Agregar o quitar conjuntos de reglas**, seleccione los conjuntos de reglas en los que desea basar su nuevo conjunto de reglas y, a continuación, haga clic en **Aceptar**.  
  
5.  Guarde el nuevo conjunto de reglas.  
  
     El nombre del nuevo conjunto de reglas se selecciona en la lista **Ejecutar este conjunto de reglas**.  Puede cambiar el nombre para mostrar del conjunto de reglas en el paso siguiente.  
  
6.  \(Opcional\) Para cambiar el nombre para mostrar del conjunto de reglas, en el menú **Ver**, haga clic en **Ventana Propiedades**.  En el cuadro **Nombre**, escriba el nombre para mostrar.  
  
7.  Para agregar, quitar o modificar reglas de análisis de código concretas del nuevo conjunto de reglas, haga clic en **Abrir**.  
  
## Modificar un conjunto de reglas  
  
#### Para modificar un conjunto de reglas en el editor de conjuntos de reglas  
  
-   Para cambiar el nombre para mostrar del conjunto de reglas, en el menú **Ver**, haga clic en **Ventana Propiedades**.  En el cuadro **Nombre**, escriba el nombre para mostrar.  Observe que el nombre para mostrar puede diferir del nombre de archivo.  
  
-   Para agregar todas las reglas del grupo a un conjunto de reglas personalizado, active la casilla del grupo.  Para quitar todas las reglas del grupo, desactive la casilla.  
  
-   Para agregar una regla concreta al conjunto de reglas personalizado, active la casilla de la regla.  Para quitar la regla del conjunto de reglas, desactive la casilla.  
  
-   Para cambiar la acción que se realiza cuando una regla se infringe en un análisis de código, haga clic en el campo **Acción** de la regla y, a continuación, seleccione uno de los siguientes valores:  
  
     **Warn**: genera una advertencia.  
  
     **Error**: genera un error.  
  
     **None**: deshabilita la regla.  Esta acción es igual que quitar la regla del conjunto de reglas.  
  
## Cambiar la presentación del editor de conjuntos de reglas  
  
#### Para agrupar, filtrar o cambiar los campos del editor de conjuntos de reglas mediante la barra de herramientas del editor  
  
-   Para expandir las reglas de todos los grupos, haga clic en **Expandir todo**.  
  
-   Para contraer las reglas de todos los grupos, haga clic en **Contraer todo.**  
  
-   Para cambiar el campo por el que se agrupan las reglas, seleccione el campo en la lista **Agrupar por**.  Para mostrar las reglas desagrupadas, seleccione **\<Ninguno\>**.  
  
-   Para agregar o quitar campos de las columnas de las reglas, haga clic en **Opciones de columna**.  
  
-   Para ocultar reglas que no se aplican a la solución actual, haga clic en **Ocultar reglas que no se aplican a la solución actual**.  
  
-   Para alternar entre mostrar y ocultar reglas que tienen asignada la acción Error, haga clic en **Mostrar reglas que pueden generar errores de análisis de código**.  
  
-   Para alternar entre mostrar y ocultar reglas que tienen asignada la acción Advertencia, haga clic en **Mostrar reglas que pueden generar advertencias de análisis de código**.  
  
-   Para alternar entre mostrar y ocultar las reglas que tienen asignada la acción **Ninguno**, haga clic en **Mostrar reglas no habilitadas**.  
  
-   Para agregar o quitar conjuntos de reglas predeterminados de Microsoft en el conjunto de reglas actual, haga clic en **Agregar o quitar conjuntos de reglas secundarios**.  
  
## Vea también  
 [Cómo: Configurar el análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Referencia del conjunto de reglas Análisis de código](../code-quality/code-analysis-rule-set-reference.md)