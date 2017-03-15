---
title: "Implementar directivas de protecci&#243;n de an&#225;lisis de c&#243;digo personalizadas para el c&#243;digo administrado | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.code.analysis.selecttfsrulesets"
  - "vs.code.analysis.browsefortfsruleset"
  - "vs.code.analysis.policyeditor"
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Implementar directivas de protecci&#243;n de an&#225;lisis de c&#243;digo personalizadas para el c&#243;digo administrado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una directiva de protección de análisis de código especifica un conjunto de reglas que los miembros de un proyecto de equipo deben ejecutar en el código fuente antes de protegerlo en el control de versiones.  Microsoft proporciona una serie de *conjuntos de reglas* estándar que agrupan el análisis de código del grupo en áreas funcionales.  Los *conjuntos de reglas de directivas de protección personalizadas* especifican un conjunto de reglas de análisis de código específicas de un proyecto de equipo.  Un conjunto de reglas se almacena en un archivo .ruleset.  
  
 Las directivas de protección se establecen en el nivel de proyecto de equipo y son especificadas por la ubicación de un archivo .ruleset en el árbol del control de versiones.  No hay ninguna restricción en cuanto a la ubicación del control de versiones del conjunto de reglas de directivas personalizadas de equipo.  
  
 El análisis de código para los proyectos de código individuales se configura en la ventana Propiedades de cada proyecto.  Un conjunto de reglas personalizadas para un proyecto de código se especifica por la ubicación física del archivo .ruleset en el equipo local.  Cuando se especifica un archivo .ruleset que se encuentra en la misma unidad como el proyecto de código, Visual Studio utiliza una ruta de acceso relativa al archivo en la configuración del proyecto.  
  
 Un ejercicio sugerido para crear un conjunto de reglas personalizadas de proyecto de equipo es almacenar el archivo .ruleset de directivas de protección en una carpeta especial que no forme parte de ningún proyecto de código.  Si almacena el archivo en una carpeta dedicada, puede aplicar permisos que restrinjan quién puede modificar el archivo de reglas, además de poder mover con facilidad la estructura de directorios que contiene el proyecto a otro directorio o equipo.  
  
## Crear el conjunto de reglas de protección personalizadas del proyecto de equipo  
 Para crear un conjunto de reglas personalizadas para un proyecto de equipo, primero cree una carpeta especial para el conjunto de reglas de directivas de protección en el **Explorador de control de código fuente**.  A continuación, cree el archivo del conjunto de reglas y agréguelo al control de versiones.  Finalmente, especifique el conjunto de reglas como la directiva de protección de análisis de código del proyecto de equipo.  
  
> [!NOTE]
>  Para crear una carpeta en un proyecto de equipo, debe asignar la raíz del proyecto de equipo a una ubicación del equipo local.  Para obtener más información, vea [Create and work with workspaces \(old\)](http://msdn.microsoft.com/es-es/db4d5692-179a-44fe-ad31-0c1c900c9cb2).  
  
#### Para crear la carpeta de control de versiones para el conjunto de reglas de directivas de protección  
  
1.  En [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], expanda el nodo del proyecto de equipo y, a continuación, haga clic en **Control de código fuente**.  
  
2.  En el panel **Carpetas**, haga clic con el botón secundario en el proyecto de equipo y seleccione **Nueva carpeta**.  
  
3.  En el panel principal Control de código fuente, haga clic con el botón secundario en **Nueva carpeta**, haga clic en **Cambiar nombre** y escriba un nombre para la carpeta del conjunto de reglas.  
  
#### Para crear el conjunto de reglas de directivas de protección  
  
1.  En el menú **Archivo**, elija **Nuevo** y, a continuación, haga clic en **Archivo**.  
  
2.  En la lista **Categorías**, haga clic en **General**.  
  
3.  En la lista **Plantillas**, haga doble clic en **Conjunto de reglas de análisis de código**.  
  
4.  Especifique las reglas que desea incluir en el conjunto de reglas y, a continuación, guarde el archivo del conjunto de reglas en la carpeta del conjunto de reglas que ha creado.  
  
     Para obtener más información, vea [Crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md)  
  
#### Para agregar el archivo del conjunto de reglas al control de versiones  
  
1.  En el **Explorador de control de código fuente**, haga clic con el botón secundario en la nueva carpeta y, a continuación, haga clic en **Agregar elementos a carpeta**.  
  
     Para obtener más información, vea [Usar el control de versiones](../Topic/Use%20version%20control.md).  
  
2.  Haga clic en el archivo del conjunto de reglas que ha creado y, a continuación, en **Finalizar**.  
  
     El archivo se agrega al control de código fuente y se desprotege para usted.  
  
3.  En la ventana de detalles **Explorador de control de código fuente**, haga clic con el botón secundario en el nombre de archivo y, a continuación, haga clic en **Proteger cambios pendientes**.  
  
4.  En el cuadro de diálogo **Proteger**, tiene la opción de agregar un comentario. A continuación, haga clic en **Proteger**.  
  
    > [!NOTE]
    >  Si ya ha configurado una directiva de protección de análisis de código para su proyecto de equipo y ha seleccionado **Exigir sólo la protección de archivos que formen parte de la solución actual**, desencadenará una advertencia de error de directiva.  En el cuadro de diálogo Error en la directiva, seleccione **Invalidar el error de la directiva y continuar la protección**.  Agregue un comentario obligatorio y haga clic en **Aceptar**.  
  
#### Para especificar el archivo del conjunto de reglas como directiva de protección  
  
1.  En el menú **Equipo**, elija **Configuración del proyecto de equipo** y, a continuación, haga clic en **Control de código fuente**.  
  
2.  Haga clic en **Directiva de protección** y, a continuación, en **Agregar**.  
  
3.  En la lista **Directiva de protección**, haga doble clic en **Análisis de código** y asegúrese de que la casilla **Exigir análisis de código para código administrado** esté activada.  
  
4.  En la lista de **Ejecutar este conjunto de reglas** , haga clic en **\<Seleccionar conjunto de reglas en el control de código fuente\>**.  
  
5.  Escriba la ruta de acceso del archivo del conjunto de reglas de directivas de protección en el control de versiones.  
  
     La ruta de acceso debe tener la sintaxis siguiente:  
  
     **$\/** `TeamProjectName` **\/** `VersionControlPath`  
  
    > [!NOTE]
    >  Puede copiar la ruta de acceso mediante uno de los siguientes procedimientos en el **Explorador de control de código fuente**:  
  
    -   En el panel **Carpetas**, haga clic en la carpeta que contiene el archivo del conjunto de reglas.  Copie la ruta de acceso del control de versiones de la carpeta que aparece en el cuadro **Código fuente** y escriba el nombre del archivo del conjunto de reglas manualmente.  
  
    -   En la ventana de detalles, haga clic con el botón secundario en el archivo del conjunto de reglas y, a continuación, haga clic en **Propiedades**.  En la pestaña **General**, copie el valor en **Nombre del servidor**.  
  
## Sincronizar los proyectos de código con el conjunto de reglas de directivas de protección  
 En el cuadro de diálogo de propiedades del proyecto de código se especifica un conjunto de reglas de directivas de protección de proyecto de equipo como configuración de proyecto de código.  Si el conjunto de reglas se encuentra en la misma unidad que el proyecto de código, se utiliza una ruta de acceso relativa para especificar el conjunto de reglas cuando se selecciona la ruta de acceso desde el cuadro de diálogo Archivo.  La ruta de acceso relativa permite pasar la configuración de propiedades del proyecto a otros equipos que utilizan estructuras de control de versiones locales similares.  
  
#### Para especificar un conjunto de reglas de proyecto de equipo como el conjunto de reglas de un proyecto de código  
  
1.  Si fuera necesario, recupere la carpeta y el archivo del conjunto de reglas de directivas de protección del control de versiones.  
  
     Puede realizar este paso en el **Explorador de control de código fuente** si hace clic con el botón secundario en la carpeta del conjunto de reglas y hace clic en **Obtener la última versión**.  
  
2.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el proyecto de código y, a continuación, haga clic en **Propiedades**.  
  
3.  Haga clic en **Análisis de código**.  
  
4.  Si fuera necesario, haga clic en las opciones adecuadas de las listas **Configuración** y **Plataforma**.  
  
5.  Para ejecutar el análisis de código cada vez que se compila el proyecto de código con la configuración especificada, active la casilla **Habilitar análisis de código al compilar \(define la constante CODE\_ANALYSIS\)**.  
  
6.  Para omitir el código en componentes de otras empresas, active la casilla **Suprimir resultados del código generado**.  
  
7.  En la lista de **Ejecutar este conjunto de reglas** , haga clic en **\<Examinar...\>**.  
  
8.  Especifique la versión local del archivo del conjunto de reglas de directivas de protección.