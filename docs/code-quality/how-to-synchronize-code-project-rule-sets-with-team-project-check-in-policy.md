---
title: "C&#243;mo: Sincronizar conjuntos de reglas del proyecto de c&#243;digo con la directiva de protecci&#243;n del proyecto de equipo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.selecttfsruleset"
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Sincronizar conjuntos de reglas del proyecto de c&#243;digo con la directiva de protecci&#243;n del proyecto de equipo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La configuración del análisis de código de los proyectos de código se sincroniza con la directiva de protección del proyecto de equipo mediante la especificación de un conjunto de reglas que contiene al menos las reglas que se especifican en el conjunto de reglas para la directiva de protección.  El responsable del equipo de desarrolladores puede indicar el nombre y la ubicación del conjunto de reglas para la directiva de protección.  Puede utilizar una de las opciones siguientes para asegurarse de que el análisis de código del proyecto utiliza el conjunto correcto de reglas:  
  
-   Si la directiva de protección utiliza uno de los conjuntos de reglas integrados de Microsoft, abra el cuadro de diálogo de propiedades del proyecto de código, muestre la página Análisis de código y seleccione el conjunto de reglas en esta página de la configuración del proyecto de código.  Los conjuntos de reglas estándar de Microsoft que se instalan automáticamente con Visual Studio son de solo lectura y no se deben editar.  Si no se editan los conjuntos de reglas, se garantiza que las reglas de la directiva y los conjuntos de reglas locales coinciden.  
  
-   Si la directiva de protección utiliza un conjunto de reglas personalizado, realice una operación Get del archivo de conjunto de reglas en el control de versiones para crear una copia local.  A continuación, especifique esta ubicación local en la configuración del análisis de código para el proyecto de código.  Las reglas tienen garantizada la coincidencia si el conjunto de reglas de la directiva de protección está actualizado.  
  
     Si asigna la ubicación del control de versiones a una carpeta local que tiene la misma relación con la raíz del proyecto de equipo que el proyecto de código, especifique la ubicación del conjunto de reglas mediante una ruta de acceso relativa.  La ruta de acceso relativa garantiza que la configuración del proyecto de código para el análisis de código se puede trasladar a otros equipos.  
  
-   Personalice una copia del conjunto de reglas para la directiva de protección de un proyecto de código.  Asegúrese de que el nuevo conjunto de reglas contiene todas las reglas de la directiva de protección y cualquier otra regla que desee incluir.  Debe asegurarse de que el conjunto de reglas personalizado incluye todas las reglas del conjunto de reglas para la directiva de protección.  
  
### Para especificar un conjunto de reglas estándar de Microsoft  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el proyecto de código y, a continuación, haga clic en **Propiedades**.  
  
2.  Haga clic en **Análisis de código**.  
  
3.  En la lista **Ejecutar este conjunto de reglas**, haga clic en el conjunto de reglas de directiva de protección.  
  
### Para especificar un conjunto de reglas de directiva de protección personalizado  
  
1.  Si es necesario, realice una operación Get del archivo de conjunto de reglas que especifica la directiva de protección.  
  
2.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el proyecto de código y, a continuación, haga clic en **Propiedades**.  
  
3.  Haga clic en **Análisis de código**.  
  
4.  En la lista de **Ejecutar este conjunto de reglas** , haga clic en **\<Examinar...\>**.  
  
5.  En el cuadro de diálogo **Abrir**, especifique el archivo de conjunto de reglas de directiva de protección.  
  
### Para crear un conjunto de reglas personalizado para un proyecto de código  
  
1.  Siga uno de los procedimientos anteriores de este tema para seleccionar la directiva de protección del proyecto de equipo en la página Análisis de código del cuadro de diálogo de configuración del proyecto.  
  
2.  Haga clic en **Abrir**.  
  
3.  Agregue o quite reglas mediante el editor de conjuntos de reglas.  
  
     Para obtener más información, vea [Crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
4.  Guarde el conjunto de reglas modificado en un archivo .ruleset del equipo local o en una ruta UNC.  
  
5.  Abra el cuadro de diálogo de propiedades del proyecto de código y muestre la página **Análisis de código**.  
  
6.  En la lista de **Ejecutar este conjunto de reglas** , haga clic en **\<Examinar...\>**.  
  
7.  En el cuadro de diálogo **Abrir**, especifique el archivo de conjunto de reglas.