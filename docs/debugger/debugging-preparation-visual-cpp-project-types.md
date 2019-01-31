---
title: Prepararse para depurar proyectos de C++ | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project templates, debugging
- Visual C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 223a04eada43d9ca69bf5f2d6b5a36ce2d7a5933
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979171"
---
# <a name="debugging-preparation-visual-c-project-types"></a>Preparación de la depuración: Tipos de proyecto de Visual C++
En esta sección se describe cómo depurar los tipos de proyectos básicos creados mediante las plantillas de proyecto de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].  
  
 Tenga en cuenta que se han agrupado en esos tipos de proyecto que crean archivos DLL como resultado [depurar proyectos DLL](../debugger/debugging-dll-projects.md) debido a las características comunes que comparten.  
  
##  <a name="BKMK_In_this_topic"></a> En este tema  
 [Valores de propiedad recomendados](#BKMK_Recommended_Property_Settings)  
  
 [Proyectos Win32](#BKMK_Win32_Projects)  
  
- [Para depurar una aplicación Win32 de C o C++](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
- [Para establecer manualmente una configuración de depuración](#BKMK_To_manually_set_a_Debug_configuration)  
  
  [Aplicaciones de Windows Forms (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a> Valores de propiedad recomendados  
 Algunas propiedades se deben establecer de la misma forma en todos los casos de depuración no administrada. En las siguientes tablas se muestran los valores de propiedades recomendados. La configuración que no se incluye puede variar entre los diferentes tipos de proyectos no administrados. Para obtener más información, consulte [configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### <a name="configuration-properties-124-cc-124-optimization-node"></a>Propiedades de configuración &#124; C o C++ &#124; nodo de optimización  
  
|Nombre de la propiedad|Parámetro|  
|-------------------|-------------|  
|**Optimization**|Establezca esta opción como **Deshabilitado (/0d)**. El código optimizado es más difícil de depurar, puesto que las instrucciones generadas no se corresponden directamente con las instrucciones de código fuente. Si detecta que el programa tiene un error que solo aparece en código optimizado, active esta configuración, pero recuerde que el código mostrado en la ventana **Desensamblado** se genera a partir del código optimizado, que posiblemente no coincida con lo que aparece en las ventanas de código fuente. Es posible que otras características, como la ejecución paso a paso, no funcionen como se espera.|  
  
### <a name="configuration-properties-124-linker-124-debugging-node"></a>Propiedades de configuración &#124; vinculador &#124; nodo depuración  
  
|Nombre de la propiedad|Parámetro|  
|-------------------|-------------|  
|**Generar información de depuración**|Siempre debería establecer esta opción en **Sí (/DEBUG)** para crear los símbolos de depuración y archivos necesarios para depurar. Cuando la aplicación entra en modo de producción, puede desactivarla.|  
  
 [En este tema](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Proyectos Win32  
 Las aplicaciones Win32 son programas tradicionales de Windows escritos en C o C++. La depuración de este tipo de aplicación en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] es muy sencilla.  
  
 Entre las aplicaciones Win32 se incluyen las aplicaciones MFC y los proyectos ATL. Utilizan API de Windows y tal vez MFC o ATL, pero no utilizan Common Language Runtime (CRL). Sin embargo, pueden llamar al código administrado que utiliza el CLR.  
  
 El procedimiento siguiente explica cómo depurar un proyecto Win32 desde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Otra manera de depurar una aplicación Win32 es iniciar la aplicación fuera de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y asociarse. Para obtener más información, consulte [adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Para depurar una aplicación Win32 de C o C++  
  
1.  Abra el proyecto en Visual Studio.  
  
2.  En el menú **Depurar**, elija **Iniciar**.  
  
3.  Depurar con las técnicas descritas en [primero analicemos el depurador](../debugger/debugger-feature-tour.md).  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> Para establecer manualmente una configuración de depuración  
  
1. En el menú **Ver**, haga clic en **Páginas de propiedades**.  
  
2. Haga clic en el nodo **Propiedades de configuración** para abrirlo, si no está abierto aún  
  
3. Seleccione **General** y establezca el valor de la fila **Resultado** en **Depurar**.  
  
4. Abra el nodo **C/C++** y seleccione **General**.  
  
    En la fila **Depurar**, especifique el tipo de información de depuración que el compilador va a generar. Entre los valores que podría elegir se incluye **Base de datos de programa (/Zi)** o **Base de datos de programa para Editar y continuar (/ZI)**.  
  
5. Seleccione **Optimización** y, en la fila **Optimización**, seleccione **Deshabilitada (/0d)** en la lista desplegable.  
  
    El código optimizado es más difícil de depurar, puesto que las instrucciones generadas no se corresponden directamente con las instrucciones de código fuente. Si detecta que el programa tiene un error que sólo aparece en código optimizado, active esta configuración, pero recuerde que el código mostrado en la ventana Desensamblado se genera a partir del código optimizado, que posiblemente no coincida con lo que aparece en las ventanas de código fuente. Es probable que características como la ejecución paso a paso muestren puntos de interrupción y puntos de ejecución incorrectos.  
  
6. Abra el nodo **Enlazador** y seleccione **Depuración**. En la primera fila **Generar**, seleccione **Sí (/DEBUG)** en la lista desplegable. Siempre establezca este valor cuando depure.  
  
   Para obtener más información, consulte[configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
   [En este tema](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Aplicaciones de Windows Forms (.NET)  
 La plantilla **Aplicación de Windows Forms (.NET)** crea una aplicación de Windows Forms de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]. Para obtener más información, vea [Cómo: crear un proyecto de aplicación para Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).  
  
 La depuración de este tipo de aplicación en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] es similar a la depuración en aplicaciones de Windows Forms administradas.  
  
 Cuando se crea un proyecto de formularios Windows Forms con la plantilla de proyecto, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea automáticamente la configuración requerida para las versiones Debug y Release. Si es necesario, puede cambiar esta configuración en el cuadro de diálogo **\<Páginas de propiedades de <nombre del proyecto>**. Para obtener más información, vea [Configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md).  
  
 Para obtener más información, consulte [configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 Otra forma de depurar una aplicación de Windows Forms consiste en iniciarla fuera de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y asociarla al depurador. Para obtener más información, vea [Asociación del depurador a un programa o programas en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 [En este tema](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Vea también  
 [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)   
 [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Asociación del depurador a un programa o programas en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Cómo: crear un proyecto de aplicación para Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100))