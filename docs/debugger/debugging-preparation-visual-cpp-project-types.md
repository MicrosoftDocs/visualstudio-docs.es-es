---
title: "Preparación de la depuración: Tipos de proyecto de Visual C++ | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8cc51e55af477edfac65b79ca29e26b720510c55
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-preparation-visual-c-project-types"></a>Preparación de la depuración: tipos de proyecto de Visual C++
En esta sección se describe cómo depurar los tipos de proyectos básicos creados mediante las plantillas de proyecto de [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].  
  
 Tenga en cuenta que los tipos de proyecto que crean archivos DLL como su resultado se han agrupado en [depurar proyectos DLL](../debugger/debugging-dll-projects.md) debido a las características comunes que comparten.  
  
##  <a name="BKMK_In_this_topic"></a> En este tema  
 [Valores de propiedades recomendados](#BKMK_Recommended_Property_Settings)  
  
 [Proyectos Win32](#BKMK_Win32_Projects)  
  
-   [Para depurar una aplicación Win32 de C o C++](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
-   [Para establecer manualmente una configuración de depuración](#BKMK_To_manually_set_a_Debug_configuration)  
  
 [Aplicaciones de Windows Forms (. NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a>Valores de propiedades recomendados  
 Algunas propiedades se deben establecer de la misma forma en todos los casos de depuración no administrada. En las siguientes tablas se muestran los valores de propiedades recomendados. La configuración que no se incluye puede variar entre los diferentes tipos de proyectos no administrados. Para obtener más información, vea [configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### <a name="configuration-properties-124-cc-124-optimization-node"></a>Propiedades de configuración &#124; C/C++ &#124; Nodo de optimización  
  
|Nombre de la propiedad|Parámetro|  
|-------------------|-------------|  
|**Optimization**|Establecido en **deshabilitado (/ 0D).** El código optimizado es más difícil de depurar, puesto que las instrucciones generadas no se corresponden directamente con las instrucciones de código fuente. Si detecta que el programa tiene un error que sólo aparece en código optimizado, puede activar esta configuración, pero recuerde que el código se muestra en el **desensamblado** ventana se genera a partir de código optimizado que posiblemente no coincida con lo que se ve en el origen en Windows. Es posible que otras características, como la ejecución paso a paso, no funcionen como se espera.|  
  
### <a name="configuration-properties-124-linker-124-debugging-node"></a>Propiedades de configuración &#124; Vinculador &#124; Nodo de depuración  
  
|Nombre de la propiedad|Parámetro|  
|-------------------|-------------|  
|**Generar información de depuración**|Siempre debe establecer esta opción en **Sí (/Debug)** para crear los símbolos de depuración y archivos necesarios para la depuración. Cuando la aplicación entra en modo de producción, puede desactivarla.|  
  
 [En este tema](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a>Proyectos Win32  
 Las aplicaciones Win32 son programas tradicionales de Windows escritos en C o C++. La depuración de este tipo de aplicación en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] es muy sencilla.  
  
 Entre las aplicaciones Win32 se incluyen las aplicaciones MFC y los proyectos ATL. Utilizan API de Windows y tal vez MFC o ATL, pero no utilizan Common Language Runtime (CRL). Sin embargo, pueden llamar al código administrado que utiliza el CLR.  
  
 El procedimiento siguiente explica cómo depurar un proyecto Win32 desde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Otra manera de depurar una aplicación Win32 es iniciar la aplicación fuera de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y asociarse. Para obtener más información, consulte [adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a>Para depurar una aplicación Win32 de C o C++  
  
1.  Abra el proyecto en Visual Studio.  
  
2.  En el **depurar** menú, elija **iniciar**.  
  
3.  Depurar con las técnicas descritas en [conceptos básicos del depurador](../debugger/debugger-basics.md).  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a>Para establecer manualmente una configuración de depuración  
  
1.  En el **vista** menú, haga clic en **páginas de propiedades**.  
  
2.  Haga clic en el **propiedades de configuración** nodo para abrirlo si aún no está  
  
3.  Seleccione **General**y establezca el valor de la **salida** fila a **depurar**.  
  
4.  Abra la **C/C++** nodo y seleccione **General**.  
  
     En el **depurar** fila se especifica el tipo de información que va a generar el compilador de depuración. Puede elegir los valores son **base de datos de programa (/Zi)** o **base de datos de programa para editar y continuar (/ZI)**.  
  
5.  Seleccione **optimización**y en el **optimización** fila, seleccione **deshabilitado (/ 0D)** en la lista desplegable.  
  
     El código optimizado es más difícil de depurar, puesto que las instrucciones generadas no se corresponden directamente con las instrucciones de código fuente. Si detecta que el programa tiene un error que sólo aparece en código optimizado, active esta configuración, pero recuerde que el código mostrado en la ventana Desensamblado se genera a partir del código optimizado, que posiblemente no coincida con lo que aparece en las ventanas de código fuente. Es probable que características como la ejecución paso a paso muestren puntos de interrupción y puntos de ejecución incorrectos.  
  
6.  Abra la **vinculador** nodo y seleccione **depuración**. En la primera **generar** fila, seleccione **Sí (/Debug)** en la lista desplegable. Siempre establezca este valor cuando depure.  
  
 Para obtener más información, consulte[configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 [En este tema](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a>Aplicaciones de Windows Forms (. NET)  
 El **aplicación de Windows Forms (. NET)** plantilla crea una [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] aplicación de Windows Forms. Para obtener más información, consulta [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 La depuración de este tipo de aplicación en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] es similar a la depuración en aplicaciones de Windows Forms administradas.  
  
 Cuando se crea un proyecto de formularios Windows Forms con la plantilla de proyecto, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea automáticamente la configuración requerida para las versiones Debug y Release. Si es necesario, puede cambiar esta configuración en el  **\<nombre del proyecto > páginas de propiedades** cuadro de diálogo. Para obtener más información, consulte [configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md).  
  
 Para obtener más información, consulte [configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 Otra forma de depurar una aplicación de Windows Forms consiste en iniciarla fuera de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y asociarla al depurador. Para obtener más información, consulte [adjuntar a un programa en ejecución o varios programas](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 [En este tema](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Vea también  
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)   
 [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Adjuntar a un programa en ejecución o varios programas](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Configuraciones Debug y Release](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Cómo: crear un proyecto de aplicación de Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)