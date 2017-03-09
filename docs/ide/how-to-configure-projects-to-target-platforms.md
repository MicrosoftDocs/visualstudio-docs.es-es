---
title: "C&#243;mo: Configurar proyectos para plataformas de destino | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "64 bits [Visual Studio]"
  - "aplicaciones de 64 bits [Visual Studio]"
  - "programación de 64 bits [Visual Studio]"
  - "CPU, de destino específicas"
  - "plataformas, CPU de destino específicas"
  - "propiedades de proyecto [Visual Studio], plataformas de destino"
  - "configuración de proyectos [Visual Studio], plataformas de destino"
  - "proyectos [Visual Studio], plataformas de destino"
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Configurar proyectos para plataformas de destino
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite configurar las aplicaciones para distintas plataformas de destino, incluidas las de 64 bits.  Para obtener más información sobre la compatibilidad con plataformas de 64 bits en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vea [Aplicaciones de 64 bits](../Topic/64-bit%20Applications.md).  
  
## Configurar plataformas de destino con el Administrador de configuración  
 El **Administrador de configuración** proporciona una forma de agregar rápidamente nuevas plataformas de destino para el proyecto.  Si selecciona una de las plataformas que se incluyen con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], las propiedades del proyecto se modifican a fin de compilarlo para esa plataforma.  
  
#### Para configurar un proyecto para una plataforma de destino de 64 bits  
  
1.  En la barra de menús, elija **Compilar**, **Administrador de configuración**.  
  
2.  En la lista **Plataforma de soluciones activas**, elija una plataforma de 64 bits para la solución de destino y, a continuación, elija el botón **Cerrar**.  
  
    1.  Si la plataforma que desea no aparece en la lista **Plataforma de soluciones activas**, elija **Nuevo**.  
  
         Aparecerá el cuadro de diálogo **Nueva plataforma de solución**.  
  
    2.  En la lista **Escriba o seleccione la nueva plataforma**, elija **x64**.  
  
        > [!NOTE]
        >  Si asigna un nuevo nombre a su configuración, tendrá que modificar la configuración del **Diseñador de proyectos** para seleccionar la plataforma correcta como destino.  
  
    3.  Si desea copiar la configuración de una configuración de plataforma existente, selecciónela y, a continuación, elija el botón **Aceptar**.  
  
 Se actualizarán las propiedades de todos los proyectos que tienen como destino la plataforma de 64 bits y la próxima compilación del proyecto se optimizará para plataformas de 64 bits.  
  
## Configurar plataformas de destino en el Diseñador de proyectos  
 El Diseñador de proyectos también proporciona una forma de configurar distintas plataformas para el proyecto de destino.  Si seleccionar una de las plataformas incluidas en la lista del cuadro de diálogo **Nueva plataforma de solución** no funciona para su solución, puede crear un nombre de configuración personalizado y modificar la configuración en el **Diseñador de proyectos** a fin de configurar el proyecto para la plataforma de destino apropiada.  
  
 La realización de esta tarea varía según el lenguaje de programación utilizado.  Para obtener más información, vea los siguientes vínculos:  
  
-   Para proyectos de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], vea [\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform).  
  
-   Para proyectos de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], vea [Compilar \(Página, Diseñador de proyectos\) \(C\#\)](../ide/reference/build-page-project-designer-csharp.md).  
  
-   Para proyectos de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], vea [\/clr \(Compilación de Common Language Runtime\)](/visual-cpp/build/reference/clr-common-language-runtime-compilation).  
  
## Vea también  
 [Descripción de las plataformas de compilación](../ide/understanding-build-platforms.md)   
 [\/platform \(Specify Output Platform\)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)   
 [Aplicaciones de 64 bits](../Topic/64-bit%20Applications.md)   
 [Compatibilidad de 64 bits del IDE de Visual Studio](../ide/visual-studio-ide-64-bit-support.md)