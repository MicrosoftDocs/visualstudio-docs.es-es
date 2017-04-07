---
title: "Cómo: Configurar proyectos para plataformas de destino | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: c9ab9bf094a57baf4a309e3064cfcea9180dfebc
ms.lasthandoff: 04/05/2017

---
# <a name="how-to-configure-projects-to-target-platforms"></a>Cómo: Configurar proyectos para plataformas de destino
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite configurar las aplicaciones para distintas plataformas de destino, incluidas las de 64 bits. Para más información sobre la compatibilidad con plataformas de 64 bits en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vea [Aplicaciones de 64 bits](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).  
  
## <a name="targeting-platforms-with-the-configuration-manager"></a>Configurar plataformas de destino con el Administrador de configuración  
 El **Administrador de configuración** proporciona una forma de agregar rápidamente nuevas plataformas de destino para el proyecto. Si selecciona una de las plataformas que se incluyen con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], las propiedades del proyecto se modifican a fin de compilarlo para esa plataforma.  
  
#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Para configurar un proyecto para una plataforma de destino de 64 bits  
  
1.  En la barra de menús, elija **Compilar**, **Administrador de configuración**.  
  
2.  En la lista **Plataforma de soluciones activas**, elija una plataforma de 64 bits para la solución de destino y luego elija el botón **Cerrar**.  
  
    1.  Si la plataforma que quiere no aparece en la lista **Plataforma de soluciones activas**, elija **Nueva**.  
  
         Aparecerá el cuadro de diálogo **Nueva plataforma de solución**.  
  
    2.  En la lista **Escriba o seleccione la nueva plataforma**, elija **x64**.  
  
        > [!NOTE]
        >  Si asigna un nuevo nombre a la configuración, es posible que tenga que modificar la configuración del **Diseñador de proyectos** para seleccionar la plataforma correcta como destino.  
  
    3.  Si quiere copiar la configuración de una configuración de plataforma actual, selecciónela y luego elija el botón **Aceptar**.  
  
 Se actualizarán las propiedades de todos los proyectos que tienen como destino la plataforma de 64 bits y la próxima compilación del proyecto se optimizará para plataformas de 64 bits.  
  
## <a name="targeting-platforms-in-the-project-designer"></a>Configurar plataformas de destino en el Diseñador de proyectos  
 El Diseñador de proyectos también proporciona una forma de configurar distintas plataformas para el proyecto de destino. Si la selección de una de las plataformas incluidas en la lista del cuadro de diálogo **Nueva plataforma de solución** no funciona para la solución, puede crear un nombre de configuración personalizado y modificar la configuración en el **Diseñador de proyectos** a fin de configurar el proyecto para la plataforma de destino apropiada.  
  
 La realización de esta tarea varía según el lenguaje de programación utilizado. Para obtener más información, vea los siguientes vínculos:  
  
-   Para proyectos de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], vea [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).  
  
-   Para proyectos de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], vea [Compilar (Página, Diseñador de proyectos) (C#)](../ide/reference/build-page-project-designer-csharp.md).  
  
-   Para proyectos de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], vea [/clr (Compilación de Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).  
  
## <a name="see-also"></a>Vea también  
 [Descripción de las plataformas de compilación](../ide/understanding-build-platforms.md)   
 [/platform (Opciones del compilador de C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)   
 [Aplicaciones de 64 bits](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Compatibilidad de 64 bits del IDE de Visual Studio](../ide/visual-studio-ide-64-bit-support.md)
