---
title: "Depuraci&#243;n administrada: valores de propiedad recomendados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurar [Visual Studio], administradas"
  - "depurar código administrado, valores de propiedades recomendados"
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
caps.latest.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 29
---
# Depuraci&#243;n administrada: valores de propiedad recomendados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Algunas propiedades se deben establecer de la misma manera para todos los escenarios de depuración administrados.  
  
 En las siguientes tablas se muestran los valores de propiedades recomendados.  
  
 Los valores no incluidos en esta lista pueden variar entre los diferentes tipos de proyectos administrados.  Por ejemplo, **Acción de inicio** se establecerá de manera diferente en un proyecto de Windows Forms que en un proyecto de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
### Propiedades de configuración en la ficha Generar \(C\#\) o Compilar \(Visual Basic\)  
  
|**Nombre de la propiedad**|**Configuración**|  
|--------------------------------|-----------------------|  
|**Definir constante DEBUG**|C\# y F\#: active la casilla.  Esto permite que la aplicación utilice la clase Debug.|  
|**Definir constante TRACE**|C\# y F\#: active la casilla.  Esto permite que la aplicación utilice la clase Trace.|  
|**Optimizar código**|C\#, F\# y Visual Basic: establezca su valor en false.  El código optimizado es más difícil de depurar, puesto que las instrucciones generadas no se corresponden directamente con las instrucciones de código fuente.  Si detecta que el programa tiene un error que sólo aparece en código optimizado, puede activar esta configuración, pero recuerde que el código mostrado en la ventana **Desensamblado** se genera a partir de código optimizado que tal vez no coincida con lo que aparece en el Editor de código.  Para depurar el código optimizado, debe desactivar Sólo mi código. \(Vea [Restringir la ejecución paso a paso a Solo mi código](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)\).<br /><br /> Para obtener más información, vea [Configuración del proyecto para configuraciones de depuración en C\#](../debugger/project-settings-for-csharp-debug-configurations.md) o [Configuración del proyecto para una configuración de depuración de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Ruta de acceso de los resultados**|Establézcalo en bin\\Debug \\.|  
|**Opciones de compilación avanzadas**|Solo Visual Basic.  Haga clic en **Avanzadas** para establecer las propiedades avanzadas que se describen en la tabla siguiente.|  
  
### Configuración de compilador avanzada \(cuadro de diálogo\)  
  
|**Nombre de la propiedad**|**Valor**|  
|--------------------------------|---------------|  
|**Habilitar optimizaciones**|Establecida en false por las razones especificadas en la opción **Optimizar código** en la tabla anterior.|  
|**Generar información de depuración**|Active esta casilla para que se establezca el marcador \/DEBUG cuando se realice la compilación, lo que generará la información necesaria para facilitar la depuración.|  
|**Definir constante DEBUG**|Active esta casilla para definir la constante `DEBUG`, que permite que la aplicación utilice la clase <xref:System.Diagnostics.Debug>.|  
|**Definir constante TRACE**|Active esta casilla para definir la constante `TRACE`, que permite que la aplicación utilice la clase <xref:System.Diagnostics.Trace>.|  
  
## Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Tipos de proyectos de C\#, F\# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)