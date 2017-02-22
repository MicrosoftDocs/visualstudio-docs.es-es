---
title: "C&#243;mo: Crear o actualizar directivas de protecci&#243;n de an&#225;lisis de c&#243;digo est&#225;ndar | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.policyeditor"
helpviewer_keywords: 
  - "análisis de código, migrar directiva de protección"
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: 29
caps.handback.revision: 29
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Crear o actualizar directivas de protecci&#243;n de an&#225;lisis de c&#243;digo est&#225;ndar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede exigir que se ejecute un análisis de código en todos los proyectos de código de un proyecto de equipo mediante la directiva de protección de análisis de código.  Un análisis de código obligatorio puede mejorar la calidad del código que se protege en la base de código.  
  
> [!NOTE]
>  Esta característica sólo está disponible si está utilizando Team Foundation Server.  
  
 Las directivas de protección de análisis de código se definen mediante los valores de configuración del proyecto de equipo y se aplican a cada proyecto de código incluido en el proyecto de equipo.  Las ejecuciones del análisis de código se configuran para los proyectos de código en el archivo de proyecto \(.xxproj\) del proyecto de código.  Las ejecuciones del análisis de código se realizan en el equipo local.  Cuando se habilita una directiva de protección de análisis de código, los archivos de un proyecto de código que se van a proteger deben compilarse después de su última edición y, en el equipo en el que se realizan los cambios, debe llevarse a cabo una ejecución del análisis de código que, como mínimo, contenga las reglas en los valores del proyecto de equipo.  
  
-   En el código administrado, la directiva de protección de establece especificando un *conjunto de reglas* que contenga un subconjunto de las reglas de análisis de código.  
  
-   En el código de C\/C\+\+, la directiva de protección requiere que se ejecuten todas las reglas de análisis de código.  Puede agregar las directivas del preprocesador para deshabilitar reglas concretas en determinados proyectos de código de su proyecto de equipo.  
  
 Después de especificar una directiva de protección en el código administrado, los miembros del equipo pueden sincronizar sus valores de análisis de código de los proyectos de código con los valores de la directiva del proyecto de equipo.  
  
### Para abrir el editor de directivas de protección  
  
1.  En Team Explorer, haga clic con el botón secundario en el nombre del proyecto de equipo, elija **Configuración del proyecto de equipo** y, a continuación, haga clic en **Control de código fuente**.  
  
2.  En el cuadro de diálogo **Control de código fuente**, seleccione la pestaña **Directiva de protección**.  
  
3.  Siga uno de estos procedimientos:  
  
    -   Haga clic en **Agregar** para crear una nueva directiva de protección.  
  
    -   Haga doble clic en el elemento **Análisis de código** existente en la lista **Tipo de directiva** para cambiar la directiva.  
  
### Para establecer las opciones de la directiva  
  
-   Seleccione o desactive las opciones siguientes:  
  
    |Opción|Descripción|  
    |------------|-----------------|  
    |**Exigir solo la protección de archivos que formen parte de la solución actual.**|El análisis de código solamente puede ejecutarse en los archivos especificados en la solución y en los archivos de configuración del proyecto.  Esta directiva garantiza que se analiza todo el código que forma parte de una solución.|  
    |**Exigir análisis de código de C\/C\+\+ \(\/analyze\)**|Exige que todos los proyectos de C o C\+\+ se compilen con la opción del compilador \/analyze para ejecutar el análisis de código antes de que puedan protegerse.|  
    |**Exigir análisis de código para código administrado**|Exige que todos los proyectos administrados ejecuten el análisis de código y se compilen antes de que se puedan proteger.|  
  
### Para especificar un conjunto de reglas administradas  
  
-   En la lista **Ejecutar este conjunto de reglas**, use uno de los siguientes métodos:  
  
    -   Seleccione un conjunto de reglas estándar de Microsoft.  
  
    -   Seleccione un conjunto de reglas personalizado, haga clic en **\<Conjunto de reglas seleccione de control de código fuente…\>**, y escriba la ruta de acceso de control de versiones del conjunto de reglas en el explorador de control de código fuente.  La sintaxis de una ruta de acceso de control de versiones es:  
  
    -   **$\/** `TeamProjectName` **\/** `VersionControlPath`  
  
    -   Para obtener más información acerca de cómo se crea e implementa un conjunto personalizado de reglas de la directiva de protección, vea [Implementar directivas de protección personalizadas para el código administrado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).  
  
## Vea también  
 [Crear y usar directivas de protección del análisis de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)