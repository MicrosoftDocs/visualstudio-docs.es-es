---
title: 'Depuración administrada: Valores de propiedad recomendados | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f63e1382d242a679ed4fac09bfb3040200fed551
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999021"
---
# <a name="managed-debugging-recommended-property-settings"></a>Depuración administrada: Valores de propiedad recomendados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Algunas propiedades se deben establecer de la misma manera para todos los escenarios de depuración administrados.  
  
 En las siguientes tablas se muestran los valores de propiedades recomendados.  
  
 Los valores no incluidos en esta lista pueden variar entre los diferentes tipos de proyectos administrados. Por ejemplo, **Acción de inicio** se establecerá de manera diferente en un proyecto de Windows Forms que en un proyecto de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Propiedades de configuración en la ficha Generar (C#) o Compilar (Visual Basic)  
  
|**Nombre de la propiedad**|**Configuración**|  
|-----------------------|-----------------|  
|**Definir constante DEBUG**|C#y F#: Establezca la casilla de verificación. Esto permite que la aplicación utilice la clase Debug.|  
|**Definir constante TRACE**|C#y F#: Establezca la casilla de verificación. Esto permite que la aplicación utilice la clase Trace.|  
|**Optimizar código**|C#, F#y Visual Basic: Se establece en false. El código optimizado es más difícil de depurar, puesto que las instrucciones generadas no se corresponden directamente con las instrucciones de código fuente. Si detecta que el programa tiene un error que solo aparece en código optimizado, puede activar esta configuración, pero recuerde que el código que se muestra en la ventana **Desensamblado** se genera a partir de código optimizado que tal vez no coincida con lo que aparece en el Editor de código. Para depurar código optimizado, debe desactivar [solo mi código](just-my-code.md).<br /><br /> Para obtener más información, consulte [configuración del proyecto para configuraciones de depuración de C#](../debugger/project-settings-for-csharp-debug-configurations.md) o [configuración del proyecto para una configuración de depuración de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Ruta de acceso de salida**|Establézcalo en bin\Debug\\.|  
|**Opciones de compilación avanzadas**|Solo Visual Basic. Haga clic en **Avanzadas** para establecer las propiedades avanzadas que se describen en la tabla siguiente.|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>Cuadro de diálogo Configuración de compilador avanzada  
  
|**Nombre de la propiedad**|**Configuración**|  
|-----------------------|-----------------|  
|**Habilitar optimizaciones**|Establecida en false por las razones especificadas en el **optimizar código** opción en la tabla anterior.|  
|**Generar información de depuración**|Active esta casilla para que se establezca el marcador /DEBUG cuando se realice la compilación, lo que generará la información necesaria para facilitar la depuración.|  
|**Definir constante DEBUG**|Active esta casilla para definir la constante `DEBUG`, que permite que la aplicación utilice la clase <xref:System.Diagnostics.Debug>.|  
|**Definir constante TRACE**|Active esta casilla para definir la constante `TRACE`, que permite que la aplicación utilice la clase <xref:System.Diagnostics.Trace>.|  
  
## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
